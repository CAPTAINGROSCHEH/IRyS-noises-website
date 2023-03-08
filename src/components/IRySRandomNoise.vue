<script setup>
  import { ref } from 'vue'

  const {soundObjs} = defineProps({
    soundObjs: Array
  });

  const idleMsg = "🎲 Click/Tap here for a random sound! 🎲";
  const isPlayed = ref(false);
  const buttonText = ref(idleMsg);

  let timeout;
  let played;
  let duration;
  let soundList = soundObjs.flat();

  // https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random
  function getRandomInt(max) {
    return Math.floor(Math.random() * max);
  }

  function playRandomSound(){
    if(isPlayed.value == true){
      console.log(played.duration)
      clearTimeout(timeout)
      played.pause()
      played.currentTime = 0;
      isPlayed.value = false;
      buttonText.value = idleMsg;
    }else{
      let randomInt = getRandomInt(soundList.length);
      let randomSound = soundList[randomInt];
      let audio = `Audios/${randomSound.category}/${randomSound.file}`;
      played = new Audio(audio);
      played.play()

      played.addEventListener("loadeddata", () => {
        duration = played.duration;
        isPlayed.value = true;
        buttonText.value = `Now playing: ${randomSound.title}`;
        timeout = setTimeout(() =>{
          isPlayed.value = false;
        }, (duration * 1000))
      });

      played.addEventListener("ended", () => {
        buttonText.value = idleMsg;
      });
    }
  }
</script>

<template> 
  <a>
    <button :class="{ played: isPlayed }" type="button" @click="playRandomSound();" :style="{'animation-duration': duration + 's'}">
        <div id="btn-overlay">
            {{ buttonText }}
        </div>
    </button>
  </a>
</template>

<style src="../assets/css/button.css" scoped />
<style scoped>
  @media screen and (max-width:  720px) {
    button{
      font-size: 4vw;
    }
  }
</style>