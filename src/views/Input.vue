<script setup>
  import Input from '@/components/Input.vue'
import { ref } from 'vue';

  const nameField = ref('')
</script>

<template>
  <h1 class="heading-1">Inputs</h1>
  <Input 
    placeholder="Write your name"
    name="Name"
    label="Your name"
    v-model:value="nameField"
  />
  <div>{{ nameField }}</div>
</template>