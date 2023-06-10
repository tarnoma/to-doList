<template>
  <div class="q-pa-md">
    <h6>To Do List</h6>
    <TodoForm />
    <TodoList />
  </div>
</template>

<script>
import TodoForm from "./TodoForm.vue";
import TodoList from "./TodoList.vue";

export default {
  name: "TodoApp",
  components: { TodoForm, TodoList },
};
</script>

<style></style>
