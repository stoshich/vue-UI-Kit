<script setup>
  import ProgressBar from '@/components/Progress/ProgressBar.vue';
  import ProgressCircle from '@/components/Progress/ProgressCircle.vue';
  import Button from '@/components/Button.vue'
  import { ref } from 'vue';

  const percent = ref(40)
  const percentCircle = ref(40)
  const clickHandlerBar = () => {
    percent.value += 10
    if(percent.value > 100) {
      percent.value = 0
    }
  }
  const clickHandlerCircle = () => {
    percentCircle.value += 10
    if(percentCircle.value > 100) {
      percentCircle.value = 0
    }
  }
</script>

<template>
  <h1 class="heading-1">Progress</h1>
  <h2 class="heading-2">Progress Bar</h2>
  <div class="line line_block">
    <progress-bar :percent="percent"/>
    <Button :label="percent < 100 ? 'Add 10%' : 'Refresh'" @click="clickHandlerBar"/>
  </div>
  <h2 class="heading-2">Progress Circle</h2>
  <div class="line line_block">
    <progress-circle :percent="percentCircle" color="danger"/>
    <Button :label="percentCircle < 100 ? 'Add 10%' : 'Refresh'" @click="clickHandlerCircle" color="danger"/>
  </div>
</template>