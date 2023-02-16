<script setup>
import IRySNoise from './components/IRySNoise.vue';
import InfoModal from './components/InfoModal.vue';

import CollabRyS from './assets/AudioLists/CollabRyS.json';
import General from './assets/AudioLists/General.json';
import IRySJP from './assets/AudioLists/IRySJP.json';
import IRySnoises from './assets/AudioLists/IRySnoises.json';
import IRySoFunny from './assets/AudioLists/IRySoFunny.json';
import WorldWideRyS from './assets/AudioLists/WorldWideRyS.json';
import IRySneeze from './assets/AudioLists/IRySneeze.json';
import IRyScream from './assets/AudioLists/IRyScream.json';
import IRySoCute from './assets/AudioLists/IRySoCute.json';
import IRySwearing from './assets/AudioLists/IRySwearing.json';
import YabaIRyS from './assets/AudioLists/YabaIRyS.json';
import YawnRyS from './assets/AudioLists/YawnRYS.json';
import IRySinging from './assets/AudioLists/IRySinging.json';

import { ref } from 'vue'

function scrollElement(id){
  let element = document.getElementById(id);
  element.scrollIntoView({behavior: 'smooth'});
}

const modalActive = ref(false);
const darkMode = ref(false);
const navActive = ref(false);

const body = document.body;

function showNav(){
    body.classList.toggle("body-navActive"); 
    navActive.value = !navActive.value;
}

function showModal(){
    body.classList.toggle("body-navActive");
    modalActive.value = !modalActive.value;
}

</script>

<template>
  <div id="mainPage-div" :class="{ darkmode: darkMode }">
    <button id="btn-information" :class="{ darkmode: darkMode }" @click="showModal()" > i </button>
    <img src="./assets/icon/darkmode.png" id="btn-darkmode" :class="{ darkmode: darkMode }" @click="darkMode = !darkMode" />
  <Transition>
    <InfoModal v-show="modalActive" @close-modal="showModal()" />
  </Transition>

  <div class="header">
    <h1 class="title" @click="showNav()"> IRySoundboard!</h1>
    <a href="https://www.youtube.com/channel/UC8rcEBzJSleTkf_-agPM20g"  target="_blank">
      <img src="https://yt3.googleusercontent.com/oC30wBZ04ibFN7AQVHAjdUX-3nS-h4DDjJBYVlsKt0OF6t1CZwrgzWlr3rS6Q12kXrw3-mt9gg=s88-c-k-c0x00ffffff-no-rj" class="logo" />
    </a>
  </div>

  <a class="burger-btn" @click="showNav()">
      <span></span>
      <span></span>
      <span></span>
    </a>
  <div class="nav-overlay" :class="{active: navActive}" >
    <div class="nav-menu" :class="{active: navActive}" @click="showNav()">
        <nav class="category-nav" @click.stop >
          <h2>Category</h2>
          <ul @click="scrollElement('General')">
            <li><a >General</a></li>
          </ul>
          <ul @click="scrollElement('IRySoFunny')">
            <li><a >IRySoFunny</a></li>
          </ul>
          <ul @click="scrollElement('IRySoCute')">
            <li><a >IRySoCute</a></li>
          </ul>
          <ul @click="scrollElement('IRySinging')">
            <li><a >IRySinging</a></li>
          </ul>
          <ul @click="scrollElement('IRyScream')">
            <li><a >IRyScream</a></li>
          </ul>
          <ul @click="scrollElement('IRySwearing')">
            <li><a >IRySwearing</a></li>
          </ul>
          <ul @click="scrollElement('YabaIRyS')">
            <li><a >YabaIRyS</a></li>
          </ul>
          <ul @click="scrollElement('IRySnoises')">
            <li><a>IRySnoises</a></li>
          </ul>
          <ul @click="scrollElement('IRySneeze')">
            <li><a>IRySneeze</a></li>
          </ul>
          <ul @click="scrollElement('YawnRyS')">
            <li><a>YawnRyS</a></li>
          </ul>
          <ul @click="scrollElement('IRySJP')">
            <li><a>IRySJP</a></li>
          </ul>
          <ul @click="scrollElement('WorldWideRyS')">
            <li><a>WorldWideRyS</a></li>
          </ul>
          <ul @click="scrollElement('CollabRyS')">
            <li><a>CollabRyS</a></li>
          </ul>
        </nav>
      </div>
    </div>
    <div >
      <div class="category" id="General">
        <h2> General</h2>
        <IRySNoise v-for="item in General" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRySoFunny">
        <h2> IRySoFunny</h2>
        <IRySNoise v-for="item in IRySoFunny" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRySoCute">
        <h2> IRySoCute</h2>
        <IRySNoise v-for="item in IRySoCute" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRySinging">
        <h2> IRySinging</h2>
        <IRySNoise v-for="item in IRySinging" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRyScream">
        <h2> IRyScream</h2>
        <IRySNoise v-for="item in IRyScream" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRySwearing">
        <h2> IRySwearing</h2>
        <IRySNoise v-for="item in IRySwearing" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="YabaIRyS">
        <h2> YabaIRyS</h2>
        <IRySNoise v-for="item in YabaIRyS" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRySnoises">
        <h2> IRySnoises</h2>
        <IRySNoise v-for="item in IRySnoises" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRySneeze">
        <h2> IRySneeze</h2>
        <IRySNoise v-for="item in IRySneeze" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="YawnRyS">
        <h2> YawnRyS</h2>
        <IRySNoise v-for="item in YawnRyS" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="IRySJP">
        <h2> IRySJP</h2>
        <IRySNoise v-for="item in IRySJP" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="WorldWideRyS">
        <h2> WorldWideRyS</h2>
        <IRySNoise v-for="item in WorldWideRyS" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
      <div class="category" id="CollabRyS">
        <h2> CollabRyS</h2>
        <IRySNoise v-for="item in CollabRyS" :category="item.category" :file="item.file" :title="item.title" class/>
      </div>
    </div>
  </div>
</template>

<style scoped>



.v-enter-active,
.v-leave-active {
  transition: opacity 0.2s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
.logo {
  border-radius: 50%;
  margin-top: 2em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #af0043);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
