<template>
  Remote App 1 - NLR
  <p>Message: {{ msg }}</p>
</template>

<script lang="ts">
import { defineProps, withDefaults } from 'vue'
  const props = withDefaults(defineProps<{msg: string}>(), {
    msg: "TEST MESSAGE",
  })
</script>