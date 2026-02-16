<script setup lang="ts">
import { ref } from 'vue'
import Hole from './Hole.vue'

defineProps<{ time: any, isGamePlaying: boolean, level: number }>()
const score = ref(0);
const holes = ref([1,2,3,4,5]);


</script>

<template>
  <div class="game-bg">
    <div class="game-header">
      <div class="scores">
        <a>LEVEL: {{ level }}</a>
        <br>
        <a>SCORE: {{ score }}</a>
      </div>
      <div class="time">
        <a>{{ time }}s</a>
      </div>
    </div>
    <div v-if="isGamePlaying" class="holes">
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
  color: black;
  font-family: Tahoma;
  font-weight: bold;
}

.game-header {
  display: flex;
}

.scores {
  text-align: left;
  padding: 5px 0 0 5px;
  font-size: 2em;
  background-color: white;
  width: 200px;
}

.time {
  position: relative;
  /* 下記2つで親要素内の中央に寄せることができるらしい */
  left: 30%;
  transform: translate(-50%);
  color: white;
  font-size: 4em;
  display: inline;
  padding: 7px;
}

.time a {
  background-color: rgb(68, 55, 19);
  border-radius: 10px;
  padding: 0 5px 0 5px;
}

</style>
