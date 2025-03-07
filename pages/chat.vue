<template>
    <section class="nes-container is-dark">
        <section class="message-list">
            <section class="message -left">
                <svg v-if="avatar" v-html="avatar" width="100" height="100"></svg>
                <div class="nes-balloon from-left is-dark">
                <input type="text" class="normal-text" v-model="sended"></input>
                </div>
            </section>

            <section class="message -right">
                <div class="nes-balloon from-right">
                <input class="normal-text" type="text" v-model="received"></input>
                </div>
                <svg v-if="avatar" v-html="avatar" width="100" height="100"></svg>
            </section>
        </section>
        <textarea id="textarea_field" class="nes-textarea"></textarea>
        <input type="text" class="nes-btn is-primary" v-model="send"></input>
    </section>
</template>

<style scoped>
    @import "nes.css/css/nes.css";
    @import "@/assets/css/chatapp-css.css";

    .normal-text {
        color: black;
        width: 100%;
    }

    .normal-text:focus {
        color: black;
    }

    section .message .-right {
        flex-direction: row-reverse;
        justify-content: flex-start;
    }

    section.message-list {
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    section .message {
        display: flex;
        align-items: center;
    }

    section .message.-left {
        flex-direction: row;
    }

    .nes-balloon {
        max-width: 300px;
        padding: 10px;
    }

    .nes-balloon.from-right {
        width: 100%;
    }

    section .message .nes-balloon {
        max-width: 300px;
    }
</style>

<script lang="ts" setup>

    const send = "Send";
    const received = "Good morning. Thou hast had a good night's sleep, I hope.";
    const sended = "Hello NES.css";

    import { createAvatar } from '@dicebear/core';
    import { adventurer } from '@dicebear/collection';
    const avatar = createAvatar(adventurer, {
    "seed": ""
    });

    const svg = avatar.toString();

</script>