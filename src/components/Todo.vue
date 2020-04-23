<template>
  <div class="todo">
    <div class="todo-card mdl-card mdl-shadow--2dp">
      <div class="mdl-card__title">
        <label class="mdl-checkbox mdl-js-checkbox mdl-js-ripple-effect" for="checkbox-1">
          <input @click="checkTodo" type="checkbox" id="checkbox-1" class="mdl-checkbox__input" />
        </label>
        <h2 class="mdl-card__title-text" :class="{completed : todo.completed}">{{todo.title}}</h2>
        <span class="mdl-chip mdl-chip--deletable">
          <button type="button" class="mdl-chip__action" @click="handledeleteTodo">
            <i class="material-icons">cancel</i>
          </button>
        </span>
      </div>
      <!-- Deletable Chip -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: ["todo"],
  methods: {
    checkTodo: function(e) {
      this.todo.completed = e.target.checked;
      /*if (e.target.checked) {
        this.todo.completed = true;
      } else {
        this.todo.completed = false;
      }*/
    },

    handledeleteTodo: function() {
      this.$root.$emit("deleteTodo", this.todo);
    }
  }
};
</script>

<style scoped>
.todo {
  margin: auto;
  width: 500px;
  padding: 10px;
  overflow: hidden;
}

.todo .completed {
  text-decoration: line-through;
  color: grey;
}
.todo .mdl-checkbox {
  display: block;
  float: left;
  width: 32px;
  height: 32px;
}

.todo-card.mdl-card {
  width: 500px;
  min-height: 50px !important;
}

.todo .mdl-card__title {
  width: 500px;
  display: block;
}

.todo .mdl-card__title-text {
  width: 300px;
  color: #333;
  font-size: 19px;
  text-align: left;
}

.todo .mdl-chip {
  padding: 0 6px;
  width: 32px;
  float: right;
}
</style>
