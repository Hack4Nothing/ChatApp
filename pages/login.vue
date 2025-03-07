<template>
    <h1>
        <input type="text" value="hello" class="normal-text">
    </h1>
    hello
    <form>
        <center>
            <div class="window">
                <div class="inactive-title-bar">

                    <h1 class="title">
                        <input type="text" v-model="a"></input>
                    </h1>

                </div>
            </div>
            <label for="text_email">Email</label><br>
            <input id="text_email" type="email" /><br>
            <label for="text_pwd">Password</label><br>
            <input id="text_pwd" type="password" /><br><br>
            <button class="btn">Login</button>
        </center>
    </form>

</template>

<style scoped>
form {
    margin-top: 15%;
}

.normal-text {
    text-align: center;
    border: none;
    outline: none;
    background: none;
    font-size: inherit;
    /* Inherit font size from parent */
    color: inherit;
    /* Inherit text color from parent */
    padding: 0;
    /* Remove padding */
    margin: 0;
    /* Remove margin */
    font-family: inherit;
    /* Use the same font family as the parent */
    width: auto;
    /* Let the input adjust its width */
}

.normal-text:focus {
    border: none;
    outline: none;
    background: none;
    font-size: inherit;
    /* Inherit font size from parent */
    color: inherit;
    /* Inherit text color from parent */
    padding: 0;
    /* Remove padding */
    margin: 0;
    /* Remove margin */
    font-family: inherit;
    /* Use the same font family as the parent */
    width: auto;
    /* Let the input adjust its width */
}
</style>

<script lang="ts" setup>
const a = "Login Now";
</script>