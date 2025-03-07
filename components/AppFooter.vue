<template>
    <div class="standard-dialog center scale-down" style="width:30rem;">
  <h1 class="dialog-text"><input type="text" class="normal-text" v-model=versionAndName></h1>
  <p class="dialog-text"> <input type="text" class="normal-text" v-model=copyrightYear>  </p>
</div>
</template>

<style scoped>
@import '@/assets/css/chatapp-css.css';
div{
    margin: auto;
    width: 95vw !important;
}
input {
    /* text-align: left; */
    width: 100% !important;
}
</style>

<script setup>
const versionAndName = "ChatApp, Version 1.0 (jan 01 2025)"
const copyrightYear = "© 2025 Apple Computer";



 </script>