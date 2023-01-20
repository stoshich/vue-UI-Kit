<script setup>
  import { ref } from 'vue';
  import Radiobutton from '../components/Radiobutton.vue';

  const tasks = ref([
    {name: 'task1', id: 't1'},
    {name: 'task2', id: 't2'},
    {name: 'task3', id: 't3'},
    {name: 'task4', id: 't4'}
  ])
  const selectedTask = ref('')
  const disabled = ref(true)
  const disabledCheck = ref(true)
</script>

<template>
  <h1 class="heading-1">Radiobutton</h1>
  <h2 class="heading-2">Basic</h2>
  <div class="line line_block">
    <p>Selected task: {{ selectedTask }}</p>
    <div v-for="task in tasks" :key="task.id">
      <radiobutton
        :id="task.id"
        :label="task.name"
        :value="task.name"
        name="tasks"
        v-model:checkedValue="selectedTask"
      />
    </div>
  </div>
  <h2 class="heading-2">Disabled</h2>
  <radiobutton
    id="disabledRadio"
    label="Disabled Radiobutton"
    value="disabledRadio"
    name="disabledRadio"
    :disabled="disabled"
    v-model:checkedValue="disabledCheck"
  />
</template>