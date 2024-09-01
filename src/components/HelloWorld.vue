<script setup lang="ts">
import { driver } from "driver.js";
import "driver.js/dist/driver.css";

defineProps<{ msg: string }>()

const driverObj = driver({
  showProgress: true, // 显示进度
  allowClose: true, // 允许关闭
  doneBtnText: "结束", // 完成按钮文本
  nextBtnText: "下一步", // 下一步按钮文本
  prevBtnText: "上一步", // 上一步按钮文本
  steps: [
    { element: '#logo', popover: { title: 'Logo', description: '标志: vite + vue', side: "left", align: 'start' } },
    { element: '#myName', popover: { title: 'Blog', description: '名称：前端杂货铺', side: "right", align: 'end' } },
    { element: '#card', popover: { title: 'Driver', description: '向导：向导按钮', side: "top", align: 'start' } },
    { element: '#end', popover: { title: 'End', description: '结束：最后一步', side: "bottom", align: 'start' } },
  ]
});
</script>

<template>
  <h1 id="myName">{{ msg }}</h1>

  <div class="card" id="card">
    <button type="button" @click=driverObj.drive();>开启向导</button>
  </div>

  <p id="end">Driver.js的使用很简单，End!</p>
</template>

<style scoped>

</style>
