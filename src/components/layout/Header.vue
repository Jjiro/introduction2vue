<template>
  <header class="header">
    <h1>Todo List</h1>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
  position: sticky;
  top: 0;
  z-index: 1;
}

.header a {
  color: #fff;
  padding-left: 5px;
}
</style>