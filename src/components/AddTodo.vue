<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo" />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
//import uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        // id: uuid.v5(),
        title: this.title,
        completed: false
      };
      //send up to parent
      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  padding: 20px 10px;
  
}

input[type="text"] {
  flex: 8;
  padding: 5px;
  border-radius: 10px;
}

input[type="submit"] {
  flex: 2;
  padding: 10px;
  justify-content: space-between;
}
</style>