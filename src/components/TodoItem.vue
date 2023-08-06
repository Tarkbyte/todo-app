<template>
  <p>{{ todo.title }}</p>
</template>

<script setup>
const props = defineProps({
  todo: {
    type: Object,
    default: () => {},
  },
});
</script>
