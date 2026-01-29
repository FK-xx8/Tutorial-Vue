<script setup lang="ts">
import { ref } from 'vue'
import Hole from './Hole.vue'

const score = ref(0);
const time = ref("00");
const holes = ref([1,2,3,4,5]);
</script>

<template>
  <div class="game-bg">
    <div class="game-header">
      <a>TIME: {{ time }}s</a>
      <br>
      <a>SCORE: {{ score }}</a>
    </div>
    <div class="holes">
      <!-- 繰り返して表示 -->
        <Hole v-for="hole in holes" num=""/>
    </div>
  </div>
</template>

<style scoped>
.game-bg {
  height: 100%;
  width: 100%;
  background-color: rgb(156, 221, 152);
}

.game-header {
  text-align: left;
  color: black;
  padding: 5px 0 0 5px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-size: 2em;
  font-weight: bold;
  background-color: white;
  width: 200px;
}

</style>
