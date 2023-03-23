<script setup>
import { ref, defineEmits } from "vue";

const newTodoData = ref("");

const btnClick = () => {
  console.log("I´ve clicked " + newTodoData.value);
};
</script>

<template>
  <div class="toDoInputDiv">
    <input
      v-model="newTodoData"
      type="text"
      class="input-todo"
      placeholder="Add a new task"
    />
    <button class="send-button" @click="btnClick">
      Add Task <i class="ri-add-circle-fill"></i>
    </button>
  </div>
</template>

<style scoped>
.input-todo {
  background-color: #262626;
  color: #f2f2f2;
  font-size: 1.8rem;
  border: 1px solid black;
  border-radius: 8px;
  width: 350px;
  height: 44px;
  padding: 0 12px;
}

.send-button {
  margin-left: 12px;
  padding: 16px 40px;
  background-color: #1e6f9f;
  color: #f2f2f2;
  font-weight: bold;
  border-radius: 8px;
  border: 0;
  cursor: pointer;
}
</style>