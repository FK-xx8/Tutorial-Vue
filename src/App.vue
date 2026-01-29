<script setup lang="ts">
import GameGround from './components/GameGround.vue'
</script>

<template>
  <div class="header">
    <h1>モグラ叩き</h1>
  </div>
  <div class="main-content">
    <div class="game-area">
      <GameGround/>
    </div>
    <div class="game-setting">
      <div class="setting-btn">
        <button class="btn">START</button>
        <button class="btn">RESTART</button>
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
  height: 88vh;
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
}

.btn {
  height: 80px;
  width: 200px;
  font-size: 40px;
  font-family: 'Impact';
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
</style>
