<script setup>
import { inject } from "vue";
import notification from "sweetalert2";

const task = inject("tasks");

const clicked = (value) => {
  task.splice(value, 1);
};

const checkStatus = (value, index) => {
  value ? clicked(index) : notification.fire("The task has to be done first!");
};
</script>
<template  >
  <ul class="task-list">
    <li class="task-item" v-for="(todo, i) in task" :key="todo.text">
      <div class="task-container">
        <i
          :class="
            todo.status
              ? ['todo-done', 'ri-checkbox-circle-line']
              : ['todo-not-done', 'ri-checkbox-blank-circle-line']
          "
          @click="todo.status = !todo.status"
          class=""
        ></i>
        <p :class="todo.status ? ['task-undone'] : ['']">
          {{ todo.text }}
        </p>
        <i @click="checkStatus(todo.status, i)" class="ri-delete-bin-line"></i>
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

.task-undone {
  text-decoration: line-through;
}

.task-container i {
  font-size: 2.5rem;
}

.todo-done {
  color: green;
}

.todo-not-done {
  color: red;
}
</style>