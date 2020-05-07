<template>
  <div class="todo-item" v-bind:class="{'is-completed':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{ todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #cacaca;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
  border-radius: 10px;
  margin: 5px;
}
input[type="checkbox"] {
  margin-right: 10px;
}

.is-completed {
  text-decoration: line-through;
  opacity: 0.5;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 10px;
  border-radius: 20%;
  float: right;
  cursor: pointer;
}

.del:hover {
  background: rgb(233, 221, 51);
  color: black;
}
</style>