<template>
  Remote App 1 - NLR
  <p>Message: {{ props.msg }}</p>
</template>

<script lang="ts">
  const props = withDefaults(defineProps(), {
    msg: "TEST MESSAGE",
  })
</script>