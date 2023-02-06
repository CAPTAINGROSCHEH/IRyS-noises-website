<script setup>


const {msg, category, file, title} = defineProps({
  msg: String,
  category: String,
  file: String,
  title: String
})

//let audio = new Audio('https://cdn.discordapp.com/attachments/865117129514680330/1071758172907380868/IRyS_dundundun.wav');

const audio = new Audio(`src/assets/Audios/${category}/${file}`);


</script>

<template>
  <h1>{{ msg }}</h1>
    
  <div class="card">
    <button type="button" @click="audio.play()">{{ title }}</button>
    <p>
      ça vient de
      <code>components/IRySNoise.vue</code> mdr
    </p>
  </div>

  <p class="read-the-docs">Catégorie : {{ category }} Fichier : {{ file }} Titre : {{ title }}</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
