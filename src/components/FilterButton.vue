<script setup lang="ts">
import type { TaskFilter } from '../types';

const props = defineProps<{
  filter: TaskFilter;
  currentFilter: TaskFilter;
}>();

const emit = defineEmits<{
  setFilter : [filter: TaskFilter]
}>();

</script>

<template>
  <button class="secondary" :class="{ contrast: props.filter === props.currentFilter }" @click="emit('setFilter', props.filter)">{{ props.filter }}</button>
</template>

<style scoped>
button {
  text-transform: capitalize;
}
</style>