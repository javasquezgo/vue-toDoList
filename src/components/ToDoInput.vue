<script setup>
import { ref, defineEmits } from "vue";

let newTodoData = ref("");

//Definimos una variable emit para mandar a llamar
//defineEmits que puede almacenar un array de
//funciones que deseamos emitir
//pero algo importante el valor que esta dentro del array o los elementos
//son los que tienes que llamar en el padre o sea
//addNewTodo va aqui, cuando envias en la funcion y en el padre con v-on
const emit = defineEmits(["addNewTodo"]);

//De ahi creamos una funcion que mande a llamar a la variable emit
//en realidad puede ser cualquiera pero convención lo dejamos asi
//de ahi acepta dos parametros: 1) el nombre del evento que definiste
//la verdad se puede llamar como sea pero busca algo para entender que hace
//2) el valor que quieras enviar al padre :v
const emitFunction = () => {
  emit("addNewTodo", {
    text: newTodoData.value,
    state: false,
  });
  newTodoData.value = "";
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
    <!--Aqui solo mandamos a llamar -->
    <button class="send-button" @click="emitFunction">
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

.send-button:hover {
  background-color: #4ea8de;
}
</style>