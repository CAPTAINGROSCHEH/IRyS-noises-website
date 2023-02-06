<script setup>
import HelloWorld from './components/HelloWorld.vue'
import IRySNoise from './components/IRySNoise.vue'
</script>

<template>
  <div>
    <a href="https://www.youtube.com/channel/UC8rcEBzJSleTkf_-agPM20g" target="_blank">
      <img src="https://yt3.googleusercontent.com/oC30wBZ04ibFN7AQVHAjdUX-3nS-h4DDjJBYVlsKt0OF6t1CZwrgzWlr3rS6Q12kXrw3-mt9gg=s88-c-k-c0x00ffffff-no-rj" class="logo" alt="Vite logo" />
    </a>
  </div>
  <IRySNoise msg="On test un petit son ici nous" category="IRySneeze" file="IRySneeze.mp3" title="IRySneeze 1" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
