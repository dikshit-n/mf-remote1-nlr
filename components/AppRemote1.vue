<template>
  Remote App 1 - NLR
  <p>Message: {{ msg }}</p>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'
defineProps<{msg: string}>()
</script>