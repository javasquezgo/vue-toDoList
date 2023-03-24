<script setup>
import { computed, provide, reactive, ref } from "vue";
import ToDoInput from "./components/ToDoInput.vue";
import Task from "./components/Task.vue";

const toDoList = reactive([
  {
    text: "Code .",
    status: false,
  },
  {
    text: "Read my books",
    status: false,
  },
  {
    text: "Work out",
    status: true,
  },
  {
    text: "Create the api",
    status: true,
  },
]);
provide("tasks", toDoList);

const totalToDo = computed(() => {
  return toDoList.length;
});

const totalDoneTask = computed(() => {
  return toDoList.filter((todo) => {
    return todo.status === true;
  }).length;
});

const updateToDoList = (newTodo) => {
  toDoList.push(newTodo);
};
</script>

<template>
  <header class="todo-header">
    <img src="./assets/Logo.svg" alt="Logo ToDo" class="header-logo" />
    <to-do-input class="header-input" @addNewTodo="updateToDoList" />
  </header>

  <section class="container">
    <div class="container-total-task">
      <p>
        ToDo List Total: <span>{{ totalToDo }}</span>
      </p>
      <p>
        ToDo List Done Total: <span>{{ totalDoneTask }}</span>
      </p>
    </div>
    <task></task>
  </section>
</template>

<style scoped>
.header-input {
  position: absolute;
  bottom: -12%;
}

section {
  margin: 40px auto;
}
</style>
