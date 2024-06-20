<script setup>
defineProps({
  message: String,
});
</script>

<template>
  <div v-show="message">
    <p class="mb-4 font-medium text-sm text-green-600 dark:text-green-400">
      {{ message }}
    </p>
  </div>
</template>