<script>
import { ref } from 'vue'

export default {
    
}

</script>

<template>
    <div class="modal-overlay" @click="$emit('close-modal')" >
        <div class="modal" @click.stop>
            <div class="modal-header">
                <h1>About</h1>
                <button class="close" @click="$emit('close-modal')" >X</button>
            </div>
            <div class="modal-body">
                <h2>What is this?</h2>
                <p>Hey, <a href="https://twitter.com/Akaridesho">Walid</a> here! I made this fan website for the smartest member of Project Hope: <a href="https://www.youtube.com/channel/UC8rcEBzJSleTkf_-agPM20g">IRyS</a>! The website was inspired by <a href="https://howsthevolu.me/">howsthevolu.me</a> and by <a href="https://kronii-cute.com/">kronii-cute.com</a>.</p>
                <p>For anyone interested in the source code, you can find it <a href="https://github.com/CAPTAINGROSCHEH/IRyS-noises-website">here</a>.</p>
                <h2>Why?</h2>
                <p>As someone who often watches IRyS live, I got used to audio clip her streams a lot for various reasons (as you see notice with all the sound categories on the website), and by seeing a various amount of soundboard websites for the other Holomembers, I had the idea to make this one since I always wanted to do a programming project for IRyS.</p>
                <h2>Credits</h2>
                <p>I would never be able to do this alone, a good amount of friends and tools helped me to make this:</p>
                <ul>
                    <li>Goose for helping me to start this project by giving me some really useful advices.</li>
                    <li><a href="https://www.youtube.com/@Pyrospower">Pyrospower</a>, <a href="https://twitter.com/Walt280">Tactician_Walt</a>, <a href="https://github.com/Warheart-1">Warheart</a>, Yayaka and lots of other people for the testing and all the advices they gave to me.</li>
                    <li><a href="https://twitter.com/kito_koruta/status/1500755335518498817?s=20">IRyS' Youtube PFP</a> by <a href="https://twitter.com/kito_koruta/">Kito Koruta</a> for the favicon and the header icon.</li>
                    <li>The font used is <a href="https://www.fontspring.com/fonts/inky-type/riffic">Riffic Free Bold</a>.</li>
                    <li>The frontend is written with <a href="https://vuejs.org/">Vue</a>.</li>
                    <li><a href="https://howsthevolu.me/">howsthevolu.me</a> and by <a href="https://kronii-cute.com/">kronii-cute.com</a> for the inspiration in the first place.</li>
                    <li>Background's image is a screenshot from <a href="https://youtu.be/-g701QOZtrc">IRyS' Kimono Reveal stream</a> during the secret ending (for Desktop version).</li>
                </ul>
                <h2>What's more?</h2>
                <p>As I said, I'm used to clip most of IRyS' streams, so I'll update the soundboard every few weeks.</p>
                <p>If you want to report an issue or ask any questions, you can find me on <a href="https://twitter.com/Akaridesho">Twitter</a>!</p>
                <h2>How many sounds are there here?</h2>
                <p>There's currently 2669 sounds! You can find the audios that were added during each update <a href="https://github.com/CAPTAINGROSCHEH/IRyS-noises-website/tree/main/src/assets/UpdateLogs" >here</a>! </p>
            </div>
        </div>
    </div>
</template>

<style scoped>

.modal h1{

    display: inline;
    padding-top: 20px;
}

</style>