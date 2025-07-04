<script setup lang="ts">
  const message = "Vue";
  const name = "rena";
  const year = new Date().getFullYear();
</script>

<template>
  <main>
    <h1>Hello, {{ message }}!</h1>
  </main>
  <footer>©️ {{ name }} {{ year }}</footer>
</template>

<style scoped>
  h1 {
    font-weight: bold;
    text-align: center;
    color: white;
  }

  footer {
    color: white;
    text-align: center;
  }
</style>
