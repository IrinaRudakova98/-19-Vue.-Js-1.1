<script>

import Item from './Item.vue';

let id = 0;
export default {
  data() {
    return {
      todos: [],
    };
  },
  components: {
    Item,
  },
  computed: {
    renderTodos() {
      return this.todos;
    },
  },
  methods: {
    addTodo(e) {
      this.todos.unshift({
        id: id++,
        content: e.target.value,
      });
      e.target.value = "";
    },
    deleteTodo(id) {
      this.todos.splice(
        this.todos.findIndex((todo) => id === todo.id),1
      );
    },
    toggleStatus(index) {
            this.todos[index].status = !this.todos[index].status;
        }
  },
};
</script>

<template>
   <section class="real-app">
    <input type="text"
    class="add-input"
    v-on:keyup.enter="addTodo"
    autofocus="autofocus"
    />
    <Item 
    v-for="todo in renderTodos" 
    :todo="todo" 
    :key="todo.id"
    v-on:del="deleteTodo"
    @toggle-status="toggleStatus(index)" />
   </section>
    
</template>

<style>
    .add-input {
  background-color: inherit;
  border: none;
  font-size: 20px;
  border-bottom: 1px solid #fff;
  color: #fff;
  padding: 20px;
  width: 400px;
}
.real-app {
  padding: 20px;
  width: 600px;
  margin: 0 auto;
  box-shadow: 0 0 5px #666;
}
</style>
