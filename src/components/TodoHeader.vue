<template>
  <div class="todo-header">
    <h2>Todo-List</h2>
    <form v-on:submit="submit">
      <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
        <input class="mdl-textfield__input" type="text" id="sample3" v-model="todo.title" />
        <label class="mdl-textfield__label" for="sample3">Enter todo</label>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "TodoHeader",
  data() {
    return {
      todo: {
        id: 0,
        title: "",
        completed: false
      }
    };
  },
  methods: {
    submit: function(event) {
      event.preventDefault();

      if (this.todo.title === "") {
        return;
      }

      const todo = {
        id: Math.floor(Math.random() * Math.floor(1000)),
        title: this.todo.title,
        completed: false
      };
      this.$root.$emit("handleTodoSubmited", todo);
      this.todo.title = "";
    }
  }
};
</script>

<style scoped>
.todo-header {
  margin: auto;
  width: 500px;
  padding: 10px;
}
.todo-header .mdl-textfield {
  width: 500px !important;
}

.todo-header .mdl-textfield__input {
  width: 100% !important;
  height: 40px;
  font-size: 20px;
}

.todo-header .mdl-textfield__label {
  width: 100% !important;
  font-size: 20px;
}
</style>
