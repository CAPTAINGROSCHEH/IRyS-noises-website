<script setup>
  import { ref } from 'vue'

  const {category, file, title} = defineProps({
    category: String,
    file: String,
    title: String
  })

  //let audio = new Audio('https://cdn.discordapp.com/attachments/865117129514680330/1071758172907380868/IRyS_dundundun.wav');
  //<p class="read-the-docs">Catégorie : {{ category }} Fichier : {{ file }} Titre : {{ title }}</p>

  const audio = `Audios/${category}/${file}`;
  const isPlayed = ref(false);
  let timeout;
  let played;
  let duration;

  function playSound(){
    if(isPlayed.value == true){
      console.log(played.duration)
      clearTimeout(timeout)
      played.pause()
      played.currentTime = 0;
      isPlayed.value = false;
    }else{
      played =  new Audio(audio);
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
  <a :href="audio" @click.stop.prevent="onClick">
    <button :class="{ played: isPlayed }" type="button" @click="playSound();" :style="{'animation-duration': duration + 's'}">
      <div id="btn-overlay">
        {{ title }}
      </div>
    </button>
  </a>
</template>

<style scoped>
  .played {
    background-image: url('../assets/img/btn-background.png');;
    background-size: 10% 100%;
    background-repeat: repeat-y;
    animation: linear;
    animation-name: play;
    border-color: #5e0136;
  }

  a {
    margin-left: 0;
    display: contents;
  }

  .read-the-docs {
    color: #888;
  }

  @keyframes play{
    0%{
      background-size: 0% 100% ;
    }

    100%{
      background-size: 100% 100%;
    }
  }
</style>
