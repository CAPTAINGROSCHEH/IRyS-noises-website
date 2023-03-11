<script setup>
  import { ref } from 'vue'

  const {soundObjs} = defineProps({
    soundObjs: Array
  });

  const idleMsg = "🎲 Click/Tap here for a random sound! 🎲";
  const isPlayed = ref(false);
  const buttonText = ref(idleMsg);
  const isNew = ref(false);

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
      isNew.value = false; 
    }else{
      let randomInt = getRandomInt(soundList.length);
      let randomSound = soundList[randomInt];
      let audio = `Audios/${randomSound.category}/${randomSound.file}`;
      played = new Audio(audio);
      played.play()
      isNew.value = randomSound.new ;

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
  <a :class="{ 'played': isPlayed}">
    <button :class="{ new: isNew }" type="button" @click="playRandomSound();" :style="{'animation-duration': duration + 's'}">
        <div id="btn-overlay">
            {{ buttonText }}
        </div>
    </button>
  </a>
</template>

<style scoped>

.played button{
    background-image: url('../assets/img/btn-background.png');
    background-size: 10% 100%;
    background-repeat: repeat-y;
    animation: linear;
    animation-name: play;
    border-color: #5e0136;
    margin-bottom: 20.36px;
  }


  .played .new{
    background-image: url('../assets/img/new-btn-background.png');
    border-color: #004b7c !important;
  }

  .new{
  filter: drop-shadow(0 0 0.2em #01a7e9);
  color: #000000;
  background-color: #00e0d5;
  }

  .new:hover {
  border-color: #d40051;
  background-color: #006ab1;
  }

  .new:active{
    background-color: #004b7c;
  }

  .new:focus,
  .new:focus-visible {
    outline: 4px auto -webkit-focus-ring-color;
  }


  @keyframes play{
    0%{
      background-size: 0% 100% ;
    }
    100%{
      background-size: 100% 100%;
    }
  }
  
@media screen and (max-width:  720px) {
  button{
    font-size: 4vw;
  }

  .played button{
    margin-bottom: 21.53px;

  }

}

</style>