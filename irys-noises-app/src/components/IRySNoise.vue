<script setup>


const {category, file, title} = defineProps({
  category: String,
  file: String,
  title: String
})

//let audio = new Audio('https://cdn.discordapp.com/attachments/865117129514680330/1071758172907380868/IRyS_dundundun.wav');
//<p class="read-the-docs">Catégorie : {{ category }} Fichier : {{ file }} Titre : {{ title }}</p>

const audio = new Audio(`src/assets/Audios/${category}/${file}`);


</script>

<template>
    
    <button type="button" @click="audio.play()">{{ title }}</button>


</template>

<style scoped>
.read-the-docs {
  color: #888;
}


</style>
