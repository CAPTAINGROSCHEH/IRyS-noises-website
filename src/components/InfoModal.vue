<script>
import { ref } from 'vue'

export default {
    
}

</script>

<template>
    <div class="modal-overlay" @click="$emit('close-modal')" >
        <div class="modal" @click.stop>
            <button class="close" @click="$emit('close-modal')" >X</button>
            <h1>About</h1>
            <p >hello itsa me, luigi, i hate css season 3, thank you forever</p>
        </div>
    </div>
</template>

<style scoped>

.modal h1{

    display: inline;
    padding-top: 20px;
}

</style>