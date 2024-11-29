<script setup lang="ts">
  defineProps<{ userInput: string }>();
</script>

<template>
  <p>{{ userInput }}</p>
</template>
