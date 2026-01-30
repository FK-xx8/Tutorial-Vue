<script setup>
import { isNullishCoalesce } from 'typescript';
import GameGround from './components/GameGround.vue'
import { ref } from 'vue';
let count = ref(10);
const first = count.value;
let timeoutNum = count.value * 1000;
let intervalId;
let isGamePlaying = false;
// スタートを押していない状態のとき

// スタートを押した時→タイマーをスタートさせる
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



// リセットを押した時→タイマーを押していない状態の時に戻す
</script>

<template>
  <div class="header">
    <h1>モグラ叩き</h1>
  </div>
  <div class="main-content">
    <div class="game-area">
      <!-- 双方向の受け渡しにはv-model！ -->
      <GameGround v-model:time="count" :isGamePlaying="isGamePlaying"/>
    </div>
    <div class="game-setting">
      <div v-if="count==first||count==0" class="setting-btn">
        <button class="btn" @click="startCount()">START</button>
        <button class="btn">RESET</button>
      </div>
      <!-- ゲーム中は押下できない -->
      <div v-else="count==first" class="setting-btn">
        <button class="btn" :disabled="true">START</button>
        <button class="btn">RESET</button>
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
</style>
