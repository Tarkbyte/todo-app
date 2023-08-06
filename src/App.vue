<template>
  <TodoItem v-for="todo in todoList" :key="todo.id" :todo="todo" />
</template>

<script setup>
import { ref, onMounted } from "vue";
import { apiClient } from "./api/apiClient";
import TodoItem from "./components/TodoItem.vue";

const todoList = ref([]);
const isLoading = ref(false);

const getTodos = async () => {
  try {
    isLoading.value = true;
    const response = await apiClient.get("/todos");

    todoList.value = response.data;
  } catch (error) {
    console.log(error);
  } finally {
    isLoading.value = false;
  }
};

onMounted(() => {
  getTodos();
});
</script>
