<script setup lang="ts">
  const message = "Vue";
  const name = "rena";
  const year = new Date().getFullYear();
</script>

<template>
  <main>
    <h1>Hello, {{ message }}!</h1>
  </main>
  <footer>
    <p>&copy; name 1234</p>
  </footer>
</template>

<style scoped>
  h1 {
    font-weight: bold;
    text-align: center;
    color: white;
  }

  footer {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    color: white;
    text-align: center;
    font-family: monospace;
  }
</style>
