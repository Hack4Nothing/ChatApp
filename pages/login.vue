<template>
    <form>
        <center>
            <div class="window">
                <div class="inactive-title-bar">

                    <h1 class="title">
                        <input class="normal-text" type="text" v-model="title"></input>
                    </h1>

                </div>
            </div>
            <div>
            <svg v-if="avatar" v-html="avatar" width="100" height="100"></svg>
            </div>
            <label for="text_username">
                <input class="normal-text" type="text" v-model="username"></input></label><br>
            <input id="text_username" type="text" v-model="r_username"/><br>
            <label for="text_pwd">
                <input class="normal-text" type="text" v-model="password"></input></label><br>
            <input id="text_pwd" type="password" /><br><br>
            
                <input class="btn" type="text" v-model="btn_login"></input>
            <br><br>
            <input class="normal-text" type="text" v-model="newuser"></input><br><br>

        </center>
    </form>

</template>

<style scoped>
@import '@/assets/css/chatapp-css.css';
form {
    margin-top: 3%;
}
</style>

<script lang="ts" setup>
    const title = "Login Now";
    const username = "Username";
    const password = "Password";
    const btn_login = "Login";
    const newuser = "New User? Register Here";
    const r_username = ref("");

    import { ref, watch } from 'vue';
    import { createAvatar } from '@dicebear/core';
    import { adventurer } from '@dicebear/collection';

    const avatar = ref<string | null>(null);

    watch(r_username, (newValue) => {
        generateAvatar(newValue);
    });

    function generateAvatar(seed: string) {
        const generatedAvatar = createAvatar(adventurer, {
        seed: seed || 'default', 
        });
        avatar.value = generatedAvatar.toString();
    }

    generateAvatar(r_username.value);
</script>