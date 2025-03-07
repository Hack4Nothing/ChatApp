<template>
    <form>
        <center>
            <div class="window">
                <div class="inactive-title-bar">

                    <h1 class="title">
                        <input class="normal-text" type="text" v-model="a"></input>
                    </h1>

                </div>
            </div>
            <label for="text_email">
                <input class="normal-text" type="text" v-model="b"></input></label><br>
            <input id="text_email" type="email" /><br>
            <label for="text_pwd">
                <input class="normal-text" type="text" v-model="c"></input></label><br>
            <input id="text_pwd" type="password" /><br><br>
            
                <input class="btn" type="text" v-model="d"></input>
        </center>
    </form>

</template>

<style scoped>
@import './assets/css/chatapp-css.css';
form {
    margin-top: 10%;
}
</style>

<script lang="ts" setup>
const a = "Login Now";
const b = "Email";
const c = "Password";
const d = "Login";
</script>