<template>
  <div id="app">
        <h1>To Do -lista</h1>
        <ToDoForm @todo-added="addToDo"></ToDoForm>
        <ul>
          <li v-for="item in ToDoItems" :key="item.id">
            <ToDoItem 
              :label="item.label"
              :done="item.done"
              :id="item.id"></ToDoItem>
          </li>
        </ul>
  </div>
</template>

<script>
import uniqueId from "lodash.uniqueid";
import ToDoItem from "./components/ToDoItem.vue";
import ToDoForm from "./components/TodoForm.vue";

export default {
  name: 'App',
  components: {
    ToDoItem,
    ToDoForm
  },
  data() {
    return {
      ToDoItems : [
        { id: uniqueId("todo-"), label: "Opiskele Vue.js", done: false },
        { id: uniqueId("todo-"), label: "Tee eka Vue.js app", done: true },
        { id: uniqueId("todo-"), label: "Pidä kivaa", done: true },
        { id: uniqueId("todo-"), label: "Tee To Do -lista", done: false },
        { id: uniqueId("todo-"), label: "Ota opintopisteet kotiin", done: false },
      ]
    }
  },
  methods: {
    addToDo(toDoLabel) {
      this.ToDoItems.push({ id: uniqueId("todo-"), label: toDoLabel, done: false })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
