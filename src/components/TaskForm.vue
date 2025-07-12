<script setup lang="ts">
import { ref } from 'vue';

const emit = defineEmits<{
  addTask: [newTask: string]
}>();

const newTask = ref('');
const errorMessage = ref('');
const formSubmit = () => {
  if (newTask.value.trim()){
    emit('addTask', newTask.value);
    newTask.value = '';
    errorMessage.value = '';
  } else {
    errorMessage.value = 'Task is required!';
  }
};
</script>

<template>
  <form @submit.prevent="formSubmit">
    <label>
      New Task
      <input type="text" name="newTask" placeholder="Wash the dishes" v-model="newTask"
        :aria-invalid="!!errorMessage || undefined" @input="errorMessage = ''">
      <small v-if="errorMessage" id="invalid-helper">
        {{ errorMessage }}
      </small>
    </label>
    <div class="button-container">
      <button>Add</button>
    </div>
  </form>
</template>