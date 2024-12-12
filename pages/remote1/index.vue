<template>
  <div>
    <AppRemote1 msg="Remote app rendered in QA" />
  </div>
</template>

<script setup lang="ts">
const { $moduleConfig } = useNuxtApp();
console.log($moduleConfig, 'config from remote 1')
  definePageMeta({
    layout: "base",
  });
</script>
