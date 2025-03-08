<template>
    <h2>
        <input class="normal-text" type="text" v-model="chat_app"></input>
    </h2>
    <h1>
        <NuxtLink to="/about">
        <input class="normal-text header" type="text" v-model="about"></input></NuxtLink>
        <NuxtLink to="/privacy">
        <input class="normal-text header" type="text" v-model="privacy_policy"></input></NuxtLink>
        <NuxtLink to="/login">
        <input class="normal-text header" type="text" v-model="login_btn"></input></NuxtLink>
    </h1>
</template>

<script lang="ts" setup>
    const chat_app = "Chat App";
    const about = "About";
    const privacy_policy = "Privacy Policy";
    const login_btn = "Login";
</script>

<style scoped>
@import '@/assets/css/chatapp-css.css';

.header {
    position: relative;
    top: -50px;
    left: 800px;
}
</style>