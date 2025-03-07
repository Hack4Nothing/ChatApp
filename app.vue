<template>
<NuxtLayout>
  <NuxtPage/>
</NuxtLayout>
</template>
<style scoped>
  @import 'https://unpkg.com/@sakun/system.css';

  .normal-text{
  border: none;
  outline: none;
  background: none;
  font-size: inherit; /* Inherit font size from parent */
  color: inherit; /* Inherit text color from parent */
  padding: 0; /* Remove padding */
  margin: 0; /* Remove margin */
  font-family: inherit; /* Use the same font family as the parent */
  width: auto; /* Let the input adjust its width */
}

.no-style-input:focus {
  border: none;
  outline: none;
  box-shadow: none; /* Remove any focus box-shadow */
}
</style>
