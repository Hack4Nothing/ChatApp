<template>
    <div id="app">
        <AppHeader />
        <slot />
        <AppFooter />
    </div>
</template>

<style scoped>
@import 'https://unpkg.com/@sakun/system.css';

#app {
    display: flex;
  flex-direction: column;
  min-height: 100vh;
  justify-content: space-between;
}
</style>