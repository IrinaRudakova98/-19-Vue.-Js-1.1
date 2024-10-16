<script>
    export default {
  
  methods: {
    deleteTodo() {
      this.$emit("del", this.todo.id);
    },
    toggleStatus() {
            this.$emit('toggle-status');
        },
  },
  props: {
    todo: {
      type: Object,
    },
  },
};
</script>

<template>
    <div class="todo-item">
        <span >{{ todo.content }}</span>
        <button @click="deleteTodo">Удалить</button>
        <input type="checkbox" @change="toggleStatus">
    </div>
    
</template>

<style>
    .todo-item {
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
  position: relative;
  font-size: 24px; 
  border-bottom: 1px solid rgba(0, 0, 0, 0.06);
}


</style>;