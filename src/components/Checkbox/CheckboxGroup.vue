<script setup>
  import Checkbox from '@/components/Checkbox/Checkbox.vue'
  const emits = defineEmits(['update:value'])
  const props = defineProps({
    value: {
      type: Array,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    options: {
      type: Array,
      required: true,
      validator: (value) => {
        const hasNameKey = value.every(option => Object.keys(option).includes('name'))
        const hasIdKey = value.every(option => Object.keys(option).includes('id'))
        return hasNameKey && hasIdKey
      }
    }
  })
  const check = (params) => {
    const udatedValues = [...props.value]
    if (params.checked) {
      udatedValues.push(params.id)
    } else {
      udatedValues.splice(props.value.indexOf(params.id), 1)
    }
    emits('update:value', udatedValues)
    }
</script>

<template>
  <div v-for="option in options" :key="option.id">
    <checkbox
      :label="option.name"
      :id="option.id"
      :value="option.name"
      :checked="value.includes(option.id)"
      group
      @updateCheckboxGroup="check"
    />
  </div>
  
</template>
