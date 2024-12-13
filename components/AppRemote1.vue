<template>
  Remote App 1 - NLR
  <p>Message: {{ msg }}</p>
  <BaseButton @click="componentError">Component Error</BaseButton>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'
defineProps<{msg: string}>()

const data = reactive({
    test: {
      name: 'test'
    }
  })
  const componentError = () => {
    data.test = undefined
  }
</script>