<script setup lang="ts">
import type { Task } from "../types";

const props = defineProps<{
    tasks: Task[];
}>();

const emit = defineEmits<{
    toggleComplete: [id: string];
    deleteTask: [id: string];
}>();
</script>

<template>
  <TransitionGroup name="task" tag="div" class="task-list">
    <article v-for="task in props.tasks" :key="task.id" class="task">
      <label>
        <input @input="emit('toggleComplete', task.id)" :checked="task.completed" type="checkbox" />
        <span :class="{ completed: task.completed }">{{
          task.title
          }}</span>
      </label>
      <button class="outline" @click="emit('deleteTask', task.id)">
        Delete
      </button>
    </article>
  </TransitionGroup>
</template>

<style scoped>
.task-list {
  margin-top: 1rem;
}

.task {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.completed {
  text-decoration: line-through;
  color: green;
}

.task-enter-active,
.task-leave-active {
  transition: all 0.5s ease;
}

.task-enter-from,
.task-leave-to {
  opacity: 0;
  transform: translateX(300px);
}
</style>
