<script setup>
import HelloWorld from './components/HelloWorld.vue';
import IRySNoise from './components/IRySNoise.vue';

import IRySneeze from './assets/AudioLists/IRySneeze.json';
import IRyScream from './assets/AudioLists/IRyScream.json';
import IRySoCute from './assets/AudioLists/IRySoCute.json';
import IRySwearing from './assets/AudioLists/IRySwearing.json';
import YabaIRyS from './assets/AudioLists/YabaIRyS.json';
import YawnRyS from './assets/AudioLists/YawnRYS.json';
import IRySinging from './assets/AudioLists/IRySinging.json';

</script>

<template>
  <div>
    <a href="https://www.youtube.com/channel/UC8rcEBzJSleTkf_-agPM20g" target="_blank">
      <img src="https://yt3.googleusercontent.com/oC30wBZ04ibFN7AQVHAjdUX-3nS-h4DDjJBYVlsKt0OF6t1CZwrgzWlr3rS6Q12kXrw3-mt9gg=s88-c-k-c0x00ffffff-no-rj" class="logo" alt="Vite logo" />
    </a>
  </div>

  
  <h1> IRyS Noises!</h1>
  <div >
    <h2> IRySneeze</h2>
    <IRySNoise v-for="item in IRySneeze" :category="item.category" :file="item.file" :title="item.title" class/>
  </div>
  <div >
    <h2> IRyScream</h2>
    <IRySNoise v-for="item in IRyScream" :category="item.category" :file="item.file" :title="item.title" class/>
  </div>
  <div >
    <h2> IRySinging</h2>
    <IRySNoise v-for="item in IRySinging" :category="item.category" :file="item.file" :title="item.title" class/>
  </div>
  <div >
    <h2> IRySoCute</h2>
    <IRySNoise v-for="item in IRySoCute" :category="item.category" :file="item.file" :title="item.title" class/>
  </div>
  <div >
    <h2> IRySwearing</h2>
    <IRySNoise v-for="item in IRySwearing" :category="item.category" :file="item.file" :title="item.title" class/>
  </div>
  <div >
    <h2> YabaIRyS</h2>
    <IRySNoise v-for="item in YabaIRyS" :category="item.category" :file="item.file" :title="item.title" class/>
  </div>
  <div >
    <h2> YawnRyS</h2>
    <IRySNoise v-for="item in YawnRyS" :category="item.category" :file="item.file" :title="item.title" class/>
  </div>

</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
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
