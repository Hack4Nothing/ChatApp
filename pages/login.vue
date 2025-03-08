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
            <NuxtLink to="/chat">
            <input class="btn" type="text" v-model="btn_login"></input></NuxtLink>
            <br><br>
            <NuxtLink to="/register">
            <input class="normal-text" type="text" v-model="newuser"></input><br><br></NuxtLink>

        </center>
    </form>

</template>

<style scoped>
@import '@/assets/css/chatapp-css.css';
form {
    margin-top: 3%;
}
</style>

<!-- <script lang="ts" setup>
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
</script> -->

<script lang="ts" setup>
import { ref, watch, onMounted } from "vue";
import { createAvatar } from "@dicebear/core";
import { adventurer } from "@dicebear/collection";

const title = ref("Login Now");
const username = ref("Username");
const password = ref("Password");
const btn_login = ref("Login");
const newuser = ref("New User? Register Here");
const r_username = ref("");
const avatar = ref<string | null>(null);

const API_URL = "http://localhost:4000/api/v1";

// 🟢 Fetch initial values from the database
async function fetchInitialValues() {
  try {
    const keys = ["title", "username", "password", "btn_login", "newuser", "r_username"];
    
    for (const key of keys) {
      const response = await fetch(`${API_URL}/get/${key}`);
      const result = await response.json();

      if (result.value) {
        switch (key) {
          case "title":
            title.value = result.value || "Login Now";
            break;
          case "username":
            username.value = result.value || "Username";
            break;
          case "password":
            password.value = result.value || "Password";
            break;
          case "btn_login":
            btn_login.value = result.value || "Login";
            break;
          case "newuser":
            newuser.value = result.value || "New User? Register Here";
            break;
          case "r_username":
            r_username.value = result.value || "";
            break;
        }
      }
    }
  } catch (error) {
    console.error("Error fetching initial values:", error);
  }
}

// 🟢 Save value to backend
async function saveValue(key: string, value: string) {
  try {
    await fetch(`${API_URL}/save`, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ key_name: key, value }),
    });
  } catch (error) {
    console.error(`Error saving ${key}:`, error);
  }
}

// 🟢 Watch each variable and update the backend when changed
watch([title, username, password, btn_login, newuser, r_username], ([newTitle, newUsername, newPassword, newBtn, newNewuser, newRusername]) => {
  saveValue("title", newTitle);
  saveValue("username", newUsername);
  saveValue("password", newPassword);
  saveValue("btn_login", newBtn);
  saveValue("newuser", newNewuser);
  saveValue("r_username", newRusername);
});

// 🟢 Generate avatar based on username
watch(r_username, (newValue) => {
  generateAvatar(newValue);
  saveValue("r_username", newValue);
});

function generateAvatar(seed: string) {
  const generatedAvatar = createAvatar(adventurer, { seed: seed || "default" });
  avatar.value = generatedAvatar.toString();
}

onMounted(() => {
  fetchInitialValues();
  generateAvatar(r_username.value);
});
</script>
