<template>
    <AppHeader />
    <textarea name="text" rows="20" id="text"></textarea>
    <AppFooter />
</template>

<style scoped>
  .app {
    width: 100%;
  }

  textarea {
    width: 100%;
  }

  textarea:focus {
    background-color: white;
    color: black;
  }
</style>

<script setup>
  definePageMeta({
    layout: 'default',  
  });
</script>