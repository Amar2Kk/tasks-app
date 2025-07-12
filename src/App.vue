<script setup lang="ts">
import { computed, ref } from 'vue';
import TaskForm from './components/TaskForm.vue';
import TasksList from './components/TasksList.vue';
import FilterButton from './components/FilterButton.vue';
import type { Task, TaskFilter } from './types';

const message = ref('Tasks App');
const tasks = ref<Task[]>([]);
const filter = ref<TaskFilter>('all');

const completedTasks = computed(() => tasks.value.reduce((total, task) => task.completed ? total + 1 : total, 0));


const addTask = (newTask: string) => {
  tasks.value.push({
    id: crypto.randomUUID(),
    title: newTask,
    completed: false,
  });
};

const toggleComplete = (id: string) => {
  const task = tasks.value.find(task => task.id === id);
  if (task) {
    task.completed = !task.completed;
  }
};

const deleteTask = (id: string) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
};

const setFilter = (newFilter: TaskFilter) => {
  filter.value = newFilter;
};

const filteredTasks = computed(() => {
  return tasks.value.filter(task => {
    if (filter.value === 'all') return true;
    if (filter.value === 'todo') return !task.completed;
    return task.completed;
  });
});
</script>

<template>
  <main>
    <h1>{{ message }}</h1>
    <TaskForm @addTask="addTask" />
    <h3 v-if="!tasks.length" class="no-tasks">No tasks yet, add one!</h3>
    <h3 v-else>{{ completedTasks }}/{{ tasks.length }} tasks completed</h3>
    <div class="button-container" v-if="tasks.length">
      <FilterButton filter="all" @setFilter="setFilter" :currentFilter="filter" />
      <FilterButton filter="todo" @setFilter="setFilter" :currentFilter="filter" />
      <FilterButton filter="completed" @setFilter="setFilter" :currentFilter="filter" />
    </div>
    <TasksList :tasks="filteredTasks" @toggleComplete="toggleComplete" @deleteTask="deleteTask" />
  </main>
</template>

<style>
main {
  max-width: 800px;
  margin: 1rem auto;
}

.button-container {
  display: flex;
  justify-content: end;
  gap: 0.5rem;
}

.no-tasks {
  text-align: center;
}
</style>