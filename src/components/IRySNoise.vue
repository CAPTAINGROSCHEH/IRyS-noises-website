<script setup>
  import { ref } from 'vue'
  import App from '../App.vue';
  
  let {category, file, title, nouveau, toggleFav } = defineProps({
    category: String,
    file: String,
    title: String,
    nouveau: Boolean,
    toggleFav: Boolean
  })

  //let audio = new Audio('https://cdn.discordapp.com/attachments/865117129514680330/1071758172907380868/IRyS_dundundun.wav');
  //<p class="read-the-docs">Catégorie : {{ category }} Fichier : {{ file }} Titre : {{ title }}</p>
  const audio = `Audios/${category}/${file}`;
  const isPlayed = ref(false);
  const isNew = nouveau;
  let timeout;
  let played;
  let duration;



  let saved = ref(localStorage.getItem('fav_' + file));

  function toggle(){
    if(saved.value == null || saved.value == false){
      saved.value = !saved.value;
      localStorage.setItem('fav_' + file, saved.value);
    }else{
      saved.value = !saved.value;
      localStorage.removeItem('fav_' + file)
    }
  }
  

  function playSound(){

    if(isPlayed.value == true){
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
  <a :href="audio" :class="{ 'played': isPlayed, saved: saved}" @click.stop.prevent="onClick" v-if="(!toggleFav) || saved">
      <button :id="title" :class="{ 'new': isNew }" type="button" @click="playSound();" :style="{'animation-duration': duration + 's'}">
        <img src="../assets/icon/starunfilled.png" @click="toggle()" :class="{hide: saved || title == 'New audios are blue!'}"/>
        <img src="../assets/icon/starfilled.png" @click="toggle()" :class="{hide: !saved}"/>

        <div id="btn-overlay">
          {{ title }}
        </div>
      </button>

  </a>
</template>

<style scoped>

  .hide{
    display: none;
  }
  
  button img{
    display:none;
  }

  button:hover img{
    position: fixed;
    width: 0.8em;
    right: 2px;
    top: 2%;
    display: block;
  }
  button:hover .hide{
    display:none
  }

  .saved button{
    border-color: #FFD700
  }

  .played button {
    background-image: url('../assets/img/btn-background.png');
    background-size: 10% 100%;
    background-repeat: repeat-y;
    animation: linear;
    animation-name: play;
    border-color: #5e0136;
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


  a {
    margin-left: 0;
    display: contents;
  }

  .played {
  background-image: url('../img/btn-background.png');
  background-size: 10% 100%;
  background-repeat: repeat-y;
  animation: linear;
  animation-name: play;
  border-color: #5e0136;
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