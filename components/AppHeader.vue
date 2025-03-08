<template>
    <h2>
        <input class="normal-text" type="text" v-model="chat_app" @blur="saveValue('chat_app', chat_app)">
    </h2>
    <h1>
<<<<<<< Updated upstream
        <NuxtLink to="/about">
        <input class="normal-text header" type="text" v-model="about"></input></NuxtLink>
        <NuxtLink to="/privacy">
        <input class="normal-text header" type="text" v-model="privacy_policy"></input></NuxtLink>
        <NuxtLink to="/login">
        <input class="normal-text header" type="text" v-model="login_btn"></input></NuxtLink>
=======
        <input class="normal-text header" type="text" v-model="about" @blur="saveValue('about', about)">
        <input class="normal-text header" type="text" v-model="privacy_policy" @blur="saveValue('privacy_policy', privacy_policy)">
        <input class="normal-text header" type="text" v-model="login_btn" @blur="saveValue('login_btn', login_btn)">
>>>>>>> Stashed changes
    </h1>
</template>

<script lang="ts" setup>
import { ref, onMounted, onUnmounted } from "vue";

const chat_app = ref("");
const about = ref("");
const privacy_policy = ref("");
const login_btn = ref("");

const API_URL = "http://localhost:4000/api/v1";
const WS_URL = "ws://localhost:4000"; // WebSocket Server URL

let socket: WebSocket | null = null;

// Fetch initial values
async function fetchInitialValues() {
    try {
        const keys = ["chat_app", "about", "privacy_policy", "login_btn"];

        for (const key of keys) {
            const response = await fetch(`${API_URL}/get/${key}`);
            const result = await response.json();

            switch (key) {
                case "chat_app":
                    chat_app.value = result.value ?? "Chat App";
                    break;
                case "about":
                    about.value = result.value ?? "About";
                    break;
                case "privacy_policy":
                    privacy_policy.value = result.value ?? "Privacy Policy";
                    break;
                case "login_btn":
                    login_btn.value = result.value ?? "Login";
                    break;
            }
        }
    } catch (error) {
        console.error("Error fetching initial values:", error);
    }
}

// Save value on blur
async function saveValue(key: string, value: string) {
    try {
        await fetch(`${API_URL}/save`, {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify({ key_name: key, value }),
        });
        console.log(`Saved ${key}:`, value);
    } catch (error) {
        console.error(`Error saving ${key}:`, error);
    }
}

// WebSocket setup
function setupWebSocket() {
    socket = new WebSocket(WS_URL);

    socket.onopen = () => {
        console.log("WebSocket connected");
    };

    socket.onmessage = (event) => {
        const data = JSON.parse(event.data);
        console.log("WebSocket Update:", data);

        if (data.key_name === "chat_app") chat_app.value = data.value;
        if (data.key_name === "about") about.value = data.value;
        if (data.key_name === "privacy_policy") privacy_policy.value = data.value;
        if (data.key_name === "login_btn") login_btn.value = data.value;
    };

    socket.onclose = () => {
        console.log("WebSocket disconnected. Reconnecting...");
        setTimeout(setupWebSocket, 3000);
    };

    socket.onerror = (error) => {
        console.error("WebSocket Error:", error);
    };
}

onMounted(() => {
    fetchInitialValues();
    setupWebSocket();
});

onUnmounted(() => {
    if (socket) socket.close();
});
</script>

<style scoped>
@import '@/assets/css/chatapp-css.css';

.header {
    position: relative;
    top: -50px;
    left: 800px;
}
</style>
