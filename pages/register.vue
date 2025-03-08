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

            <label for="text_email">
            <input class="normal-text" type="text" v-model="email"></input></label><br>
            <input id="text_email" type="text" /><br>

            <label for="text_pwd">
            <input class="normal-text" type="text" v-model="password"></input></label><br>
            <input id="text_pwd" type="password" /><br>

            <label for="text_phone">
            <input class="normal-text" type="text" v-model="phone"></input></label><br>
            <input id="text_phone" type="text"/><br>

            <label for="otp_verification">
            <input class="normal-text otp-verification" type="text" v-model="otp"></input></label><br>
            <input id="otp_verification" type="text"/><br><br>
            <NuxtLink to="/login">
            <input class="btn" type="text" v-model="register"></input></NuxtLink>
        </center>
    </form>
</template>

<script lang="ts" setup>
    const title = "Register Now";
    const username = "Username";
    const  email= "Email";
    const password = "Password";
    const phone = "Phone";
    const otp = "Sorry! Currently server is down. Your OTP is ";
    const r_username = ref("");
    const register = "Register";

    import { ref, watch } from 'vue';
    import { createAvatar } from '@dicebear/core';
    import { adventurer } from '@dicebear/collection';

    const avatar = ref<string | null>(null);

    watch(r_username, (newValue) => {
        generateAvatar(newValue);
    });

    function generateAvatar(seed: string) {
        const generatedAvatar = createAvatar(adventurer, {
        seed: seed || 'default', // If empty, use a default seed
        });
        avatar.value = generatedAvatar.toString();
    }

    generateAvatar(r_username.value);
</script>

<style scoped>
@import '@/assets/css/chatapp-css.css';
form {
    margin-top: 3%;
}

.otp-verification {
    width: 100%;
}

.otp-verification:focus {
    width: 100%;
}
</style>