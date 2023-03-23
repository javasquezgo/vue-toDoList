<script setup>
import { inject } from "vue";
import "remixicon/fonts/remixicon.css";

const task = inject("tasks");
</script>
<template  >
  <ul class="task-list">
    <li class="task-item" v-for="(todo, i) in task" :key="i">
      <div class="task-container">
        <i class="ri-checkbox-blank-circle-line"></i>
        <p>{{ todo.text }}</p>
        <i class="ri-delete-bin-line"></i>
      </div>
    </li>
  </ul>
</template>

<style scoped>
.task-list {
  list-style: none;
  margin-top: 20px;
}

.task-item {
  width: 100%;
  height: 72px;
  background-color: #262626;
  border-radius: 8px;
  margin-bottom: 12px;
}

.task-container {
  height: 100%;
  display: grid;
  grid-template-columns: 1fr 3fr 1fr;
  justify-items: center;
  align-items: center;
  color: #f2f2f2;
  font-size: 1.4rem;
  text-align: left;
}
</style>