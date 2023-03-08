<style src="../assets/css/button.css"/>
<script setup>
  import { ref } from 'vue'

  const {soundObjs} = defineProps({
    soundObjs: Array
  });

  const isPlayed = ref(false);
  let timeout;
  let played;
  let duration;
  console.log(soundObjs);
  let soundList = soundObjs.flat();
  console.log(soundList);
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
    }else{
      let randomInt = getRandomInt(soundList.length);
      let randomSound = soundList[randomInt];
      let audio = `Audios/${randomSound.category}/${randomSound.file}`;
      played = new Audio(audio);
      played.play()

      played.addEventListener("loadeddata", () => {
        duration = played.duration
        isPlayed.value = true;
        timeout = setTimeout(() =>{
          isPlayed.value = false
        }, (duration * 1000))
      })
    }
  }
</script>

<template> 
    <button :class="{ played: isPlayed }" type="button" @click="playRandomSound();" :style="{'animation-duration': duration + 's'}">
        <div id="btn-overlay">
            🎲 Click/Tap here for a random sound! 🎲
        </div>
    </button>
</template>