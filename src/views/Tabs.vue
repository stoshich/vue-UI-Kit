<script setup>
  import Tabs from '@/components/Tabs.vue'
import { ref } from 'vue';

  const tabs = [
    {name: 'About', label: 'О проекте'},
    {name: 'Vue', label: 'О Vue'},
    {name: 'React', label: 'О React'},
  ]
  const selectedTab = ref('Vue')
  const changeTab = (tabName) => {
    selectedTab.value = tabName
  }
</script>

<template>
  <h1 class="heading-1">Tabs</h1>
  <Tabs
    :names="tabs"
    :selectedTab="selectedTab"
    @changeTab="changeTab"
  >
  <div v-if="selectedTab === 'About'">
      Lorem ipsum dolor sit amet.
    </div>
    <div v-if="selectedTab === 'Vue'">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Molestiae, dolor?
    </div>
    <div v-if="selectedTab === 'React'">
      Lorem ipsum, dolor sit amet consectetur adipisicing elit. Molestias modi in placeat. Illo, deserunt tenetur!
    </div>
  </Tabs>
</template>