<template>
  Remote App 1 - NLR
  <p>Message: {{ msg }}</p>
  <p>{{ data.test.test }}</p>
  <BaseButton @click="componentError">Component Error</BaseButton>
</template>

<script setup>
import { defineProps } from 'vue'
defineProps()

const data = reactive({
    test: {
      name: 'test'
    }
  })
  const componentError = () => {
    data.test = undefined
  }
</script>