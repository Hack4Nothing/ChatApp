<template>
    <div class="window-container">
        <div class="user-list">
            <div class="title-bar">
                <button aria-label="Close" class="close"></button>
                <h1 class="title">
                    <input type="text" class="normal-text" v-model="users" placeholder="Enter username" />
                </h1>
                <button aria-label="Resize" class="resize"></button>
            </div>
            <div class="separator"></div>
            <div class="window-pane">
                <input type="text" class="normal-text" v-model="users" placeholder="Enter username" />
            </div>
        </div>
        <section class="chat-container">
            <section class="nes-container is-dark">
                <section class="message-list">
                    <section class="message -left">
                        <svg v-if="avatar" v-html="avatar" width="100" height="100"></svg>
                        <div class="nes-balloon from-left is-dark">
                            <textarea class="normal-text" v-model="sended" placeholder="Type a message"></textarea>
                        </div>
                    </section>
                    <section class="message -right">
                        <div class="nes-balloon from-right">
                            <textarea class="normal-text" v-model="received" placeholder="Message received"></textarea>
                        </div>
                        <svg v-if="avatar" v-html="avatar" width="100" height="100"></svg>
                    </section>
                </section>
                <textarea id="textarea_field" class="nes-textarea" placeholder="Type your message"></textarea>
                <input type="text" class="nes-btn is-primary" v-model="send" placeholder="Send"></input>
            </section>
        </section>
    </div>
</template>

<style scoped>
    @import "nes.css/css/nes.css";
    @import "@/assets/css/chatapp-css.css";

    .window-container {
        display: flex;
        justify-content: space-between;
        gap: 20px;
        height: auto;
    }

    .user-list {
        flex: 1;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        height: 60vh;  
        padding: 10px;
        overflow-y: auto;
    }

    .chat-container {
        flex: 3;
        display: flex;
        flex-direction: column;
        height: 100%;
    }

    .normal-text {
        color: black;
        width: 100%;
        white-space: normal;
        word-wrap: break-word;
        resize: none;
    }

    .normal-text:focus {
        color: black;
    }

    section.message.-right {
        flex-direction: row-reverse;
        justify-content: flex-start;
    }

    section.message-list {
        display: flex;
        flex-direction: column;
        gap: 10px;
        overflow-y: auto;
        flex: 1; 
    }

    section.message {
        display: flex;
        align-items: center;
    }

    section.message.-left {
        flex-direction: row;
    }

    .nes-balloon {
        max-width: 300px;
        padding: 10px;
        word-wrap: break-word;
    }

    .nes-balloon.from-right {
        width: 100%;
    }

    section .message .nes-balloon {
        max-width: 300px;
    }

    #textarea_field {
        width: 100%;
        margin-top: 10px;
        padding: 10px;
        resize: none;
    }

    .nes-btn.is-primary {
        width: 100%;
        margin-top: 10px;
    }
</style>

<script lang="ts" setup>
    const send = "Send";
    const received = "Good morning. Thou hast had a good night's sleep, I hope.";
    const sended = "Hello NES.css";
    const users = "Users";

    import { createAvatar } from '@dicebear/core';
    import { adventurer } from '@dicebear/collection';
    const avatar = createAvatar(adventurer, {
        "seed": ""
    });

    const svg = avatar.toString();
</script>
