<template>
  Remote App 1 - NLR
  <p>Message: {{ props.msg }}</p>
</template>

<script lang="ts">
import { defineProps, withDefaults } from 'vue'
  const props = withDefaults(defineProps(), {
    msg: "TEST MESSAGE",
  })
</script>