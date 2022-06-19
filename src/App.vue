<template>
  <!-- 为 ECharts 准备一个定义了宽高的 DOM -->
  <div class="box">
    <BasicLineChart :data='data'/>
  </div>
  <div class="box">
    <SmoothedLineChart :data='data'/>
  </div>
</template>

<script setup lang="ts">
import BasicLineChart from './components/BasicLineChart.vue'
import SmoothedLineChart from './components/SmoothedLineChart.vue'

let data:Array<any> = [150, 230, 224, 218, 135, 147, 260]
    
</script>

<style>
.box {
  width: 800px;
  height: 400px;
  background-color: rgb(255, 255, 255);
  box-shadow: 0 0 20px -10px #333;
  margin: 10px;
  border-radius: 10px;
}
</style>