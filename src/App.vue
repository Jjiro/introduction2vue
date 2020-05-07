<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <Footer />
    <!--<router-view> -->
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import axios from "axios";
import Footer from "./components/layout/Footer";

export default {
  name: "App",
  components: {
    Header,
    Todos,
    AddTodo,
    Footer
  },
  data() {
    return {
      todos: [
        /* {
          id: 1,
          title: "Todo One",
          completed: true
        },
        {
          id: 2,
          title: "Todo Two",
          completed: false
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        },
        {
          id: 4,
          title: "Todo Four",
          completed: true
        },
        {
          id: 5,
          title: "Todo Five",
          completed: true
        }*/
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/todos/${id}`)
        .then((this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(res => (this.todos = [...this.todos, res.data]))
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.5;
}

.btn {
  display: inline-block;
  border-block: none;
  background: rgb(5, 94, 24);
  padding: 7px 20px;
  cursor: pointer;
  color: white;
  border-radius: 10px;
}

.btn:hover {
  background: rgb(233, 221, 51);
  color: black;
}
.footer {
  position: absolute;
}
</style>
