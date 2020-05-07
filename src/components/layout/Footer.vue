
<template>
  <footer class="footer">
    <v-footer absolute class="font-weight-medium">
      <v-col class="text-center" cols="12">
        <strong>©</strong>
        {{ new Date().getFullYear() }} —
        <strong>Jjiro</strong>
      </v-col>
    </v-footer>
  </footer>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style scoped>
.footer {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 20px;
  top: 43vh;
  position: relative;
}

.footer a {
  color: #fff;
  padding-left: 5px;
}
</style>