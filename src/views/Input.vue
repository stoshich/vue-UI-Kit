<script setup>
  import Input from '@/components/Input.vue'
  import Button from '@/components/Button.vue'
import { computed, ref } from 'vue';
import useVulidate from '@vuelidate/core'
import {email, helpers, maxLength, minLength, numeric, sameAs, required} from '@vuelidate/validators'

  const nameField = ref('')
  const emailField = ref('')
  const ageField = ref('')
  const passwordField = ref('')
  const confirmPassword = ref('')

  const rules = computed(() => ({
    nameField: {
      minLength: minLength(3),
      required: required
    },
    emailField: {
      email: email,
      required: required
    },
    ageField: {
      maxLength: maxLength(3),
      numeric: numeric,
      required: required
    },
    confirmPassword: {
      sameAsPassword: helpers.withMessage('Passwords muts be the same', sameAs(passwordField)),
      required: required
    }
  }))
  const v = useVulidate(rules, {nameField, emailField, ageField, confirmPassword})
  const submitHandler = () => {
    v.value.$touch()
    if (v.value.$error) return
    alert('Form submitted')
  }
</script>

<template>
  <h1 class="heading-1">Inputs</h1>
  <form @submit.prevent="submitHandler">
    <Input 
    placeholder="Write your name"
    name="Name"
    label="Your name"
    v-model:value="v.nameField.$model"
    :errors="v.nameField.$errors"
  />
  <Input 
    placeholder="Write your email"
    name="Email"
    label="Your email"
    v-model:value="v.emailField.$model"
    :errors="v.emailField.$errors"
  />
  <Input 
    placeholder="Write your age"
    name="Age"
    label="Your age"
    v-model:value="v.ageField.$model"
    :errors="v.ageField.$errors"
  />
  <Input 
    placeholder="Write your password"
    name="password"
    label="Your password"
    v-model:value="passwordField"
    type="password"
  />
  <Input 
    placeholder="Repeat your password"
    name="confirm"
    label="Confirm your password"
    v-model:value="v.confirmPassword.$model"
    :errors="v.confirmPassword.$errors"
    type="password"
  />
  <Button label="Submit" color="primary"/>
  </form>
</template>