<script setup>
    import Checkbox from "@/components/Checkbox/Checkbox.vue"
    import CheckboxGroup from "@/components/Checkbox/CheckboxGroup.vue";
    import {ref} from 'vue'

    const checkedActive = ref(true)
    const disabledCheckbox = ref(true)
    const checkedDisabled = ref(true)

    const todoList = ref([
        {name: 'todo 1', id: 't1'},
        {name: 'todo 2', id: 't2'},
        {name: 'todo 3', id: 't3'},
        {name: 'todo 4', id: 't4'}
    ])
    const selectedTodos = ref(['t1'])
</script>

<template>
    <h1 class="heading-1">Checkbox</h1>
    <h2 class="heading-2">Active Checkbox</h2>
    <div class="line">
        <checkbox
            label="Active Checkbox"
            id="activeCheckbox"
            name="activeCheckbox"
            value="test1"
            v-model:checked="checkedActive"
        />
    </div>
    <h2 class="heading-2">Disabled Checkbox</h2>
    <div class="line">
        <checkbox
            label="Disabled Checkbox"
            id="disabledCheckbox"
            name="disabledCheckbox"
            value="test2"
            :disabled="disabledCheckbox"
            v-model:checked="checkedDisabled"
        />
    </div>
    <h2 class="heading-2">Group Checkbox</h2>
    <div class="line_block">
        <p>Selected Todos {{ selectedTodos }}</p>
        <checkbox-group name="todos" v-model:value="selectedTodos" :options="todoList"/>
    </div>
</template>