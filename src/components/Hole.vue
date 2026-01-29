<script setup lang="ts">
// import { ref } from 'vue'
defineProps<{ num: string }>()
</script>
<template>
    <button class="hole">
        <a>{{ num }}</a>
    </button>
</template>
<style>
.hole {
    margin: 200px 5px 5px 0;
    width: 150px;
    height: 250px;
    background-color: rgb(255, 127, 80);
}

.hole:active {
    background-color: rgb(218, 109, 69);
}
</style>