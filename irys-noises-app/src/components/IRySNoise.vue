<script setup>
import { ref } from 'vue'


const {category, file, title} = defineProps({
  category: String,
  file: String,
  title: String
})

//let audio = new Audio('https://cdn.discordapp.com/attachments/865117129514680330/1071758172907380868/IRyS_dundundun.wav');
//<p class="read-the-docs">Catégorie : {{ category }} Fichier : {{ file }} Titre : {{ title }}</p>

const audio = new Audio(`src/assets/Audios/${category}/${file}`);
let isPlayed = ref(false);
let timeout;

function playSound(sound){
  if (!this.isPlayed) {
    sound.play();
    this.isPlayed = true;
    timeout = setTimeout(()=> {
      this.isPlayed = false;
    }, sound.duration * 1000)
  }
  else {
    clearTimeout(timeout)
    sound.pause();
    sound.currentTime = 0;
    this.isPlayed = false;
  }
}

</script>

<template>
    <button :class="{ played: isPlayed }" type="button" @click="playSound(audio);">{{ title }}</button>
</template>

<style scoped>
.played {
  background-color: #5e0136;
}

.read-the-docs {
  color: #888;
}


</style>
