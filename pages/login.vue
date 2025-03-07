<template>

<form>
    <center>
        <div class="window">
        <div class="inactive-title-bar">

            <h1 class="title">
                <input type="text" v-model="a"></input></h1>

        </div>
        </div>
        <label for="text_email">Email</label><br>
        <input id="text_email" type="email"/><br>
        <label for="text_pwd">Password</label><br>
        <input id="text_pwd" type="password"/><br><br>
        <button class="btn">Login</button>
    </center>
</form>

</template>

<style scoped>
    form {
        margin-top: 15%;
    }
</style>

<script lang="ts" setup>
    const a = "Login Now";
</script>