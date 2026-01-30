<script setup>
import { isNullishCoalesce } from 'typescript';
import GameGround from './components/GameGround.vue'
import { ref } from 'vue';
let count = ref(10);
let intervalId;
let isGamePlaying = false;
let level = ref(1);

// カウントが開始
function startCount() {
  if (isGamePlaying === false) {
    isGamePlaying = true;
  }
  console.log(isGamePlaying);
  intervalId ??= setInterval(decreaceCount, 1000);
}

function decreaceCount() {
  count.value = count.value - 1;
  console.log(count);

  if (count.value <= 0){
    console.log("終了");
    isGamePlaying = false;
    clearInterval(intervalId);
  };

  return count;
}

// リセットは、タイマーを戻すことで実現可能？

</script>

<template>
  <div class="header">
    <h1>モグラ叩き</h1>
  </div>
  <div class="main-content">
    <div class="game-area">
      <!-- 双方向の受け渡しにはv-model！ -->
      <GameGround v-model:time="count" :isGamePlaying="isGamePlaying" :level="level"/>
    </div>
    <div class="game-setting">
      <div v-if="!isGamePlaying" class="setting-btn">
        <button class="btn" @click="startCount()">START</button>
        <button class="btn">RESET</button>
      </div>
      <!-- ゲーム中は押下できない -->
      <div v-else="isGamePlaying" class="setting-btn">
        <button class="btn" :disabled="true">START</button>
        <button class="btn">RESET</button>
      </div>
      <div v-if="!isGamePlaying">
        <p>難易度：LEVEL.{{ level }}</p>
        <button class="btn green" @click="level = 1">level.1</button>
        <button class="btn blue" @click="level = 2">level.2</button>
        <button class="btn red" @click="level = 3">level.3</button>
      </div>
    </div>
  </div>
</template>

<style> 
.header {
  background-color: rgb(109, 74, 3);
  height: auto;
  width: 100%;
}

.header h1{
  color: white;
  font-size: 50px;
  padding: 10px 0;
  text-align: center;
}

.main-content {
  width: auto;
  height: auto;
  background-color: rgb(255, 228, 194);
  padding-top: 30px;
}

.game-area {
  width: 1000px;
  height: 600px;
  background-color: white;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}

.game-setting {
  padding-top: 20px;
  text-align: center;
  padding-bottom: 30px;
}

.btn {
  height: 80px;
  width: 200px;
  font-size: 40px;
  font-family: Tahoma;
  font-weight: bold;
  margin: 0 20px;
  color: white;
  background-color: rgb(109, 74, 3);
  border-radius: 10px;
  border: none;
  box-shadow: 0 4px 0 rgb(83, 56, 2);
}
.btn:hover {
  transform: translateY(4px);
  box-shadow: none;
  background-color: rgb(83, 56, 2);
}
.btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: translateY(4px);
  box-shadow: none;
  background-color: rgb(109, 74, 3);
}

.game-setting p {
  margin-top: 20px;
  font-family: Tahoma;
  font-size: 2em;
  font-weight: bold;
  padding-top: 5px;
  padding-bottom: 5px;
  margin-bottom: 10px;
  background-color: rgb(211, 145, 14);
}

.green {
  background-color: rgb(3, 109, 21);
  box-shadow: 0 4px 0 rgb(4, 82, 17);

}
.green:hover {
  background-color: rgb(4, 82, 17);
}

.blue {
  background-color: rgb(58, 64, 148);
  box-shadow: 0 4px 0 rgb(41, 46, 112);

}
.blue:hover {
  background-color: rgb(41, 46, 112);
}

.red {
  background-color: rgb(151, 47, 47);
  box-shadow: 0 4px 0 rgb(99, 22, 22);

}
.red:hover {
  background-color: rgb(99, 22, 22);
}
</style>
