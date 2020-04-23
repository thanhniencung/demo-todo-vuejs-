<template>
  <div class="todo-list">
    <Todo v-for="todo in todoList" :key="todo.id" :todo="todo" />
  </div>
</template>

<script>
import Todo from "./Todo.vue";

export default {
  name: "TodoList",
  components: {
    Todo
  },
  data() {
    return {
      todoList: []
    };
  },
  mounted() {
    this.$root.$on("handleTodoSubmited", todo => {
      console.log(`>>> ${todo.title}`);
      this.todoList.push(todo);
    });

    this.$root.$on("deleteTodo", todo => {
      const index = this.todoList.indexOf(todo);
      if (index > -1) {
        this.todoList.splice(index, 1);
      }
    });
  }
};
</script>

<style scoped>
</style>
