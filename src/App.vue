<template>
  <div id="app">
        <h1>To Do -lista</h1>
        <ToDoForm @todo-added="addToDo"></ToDoForm>
        <ul :aria-labelledby="list-summary" class="stack-large">
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
    margin-top: 0;
    margin-bottom: 0;
  }
  .stack-small > * + * {
    margin-top: 1.25rem;
  }
  .stack-large > * + * {
    margin-top: 2.5rem;
  }
  @media screen and (min-width: 550px) {
    .stack-small > * + * {
      margin-top: 1.4rem;
    }
    .stack-large > * + * {
      margin-top: 2.8rem;
    }
  }
  /* End global styles */
  #app {
    background: #fff;
    margin: 2rem 0 4rem 0;
    padding: 1rem;
    padding-top: 0;
    position: relative;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.2), 0 2.5rem 5rem 0 rgba(0, 0, 0, 0.1);
  }
  @media screen and (min-width: 550px) {
    #app {
      padding: 4rem;
    }
  }
  #app > * {
    max-width: 50rem;
    margin-left: auto;
    margin-right: auto;
  }
  #app > form {
    max-width: 100%;
  }
  #app h1 {
    display: block;
    min-width: 100%;
    width: 100%;
    text-align: center;
    margin: 0;
    margin-bottom: 1rem;
  }
</style>
