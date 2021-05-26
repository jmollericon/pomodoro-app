<template>
  <div id="app">
    <router-view class="app-container"/>
  </div>
</template>

<style lang="scss">
@import '@/styles/reset';
@import '@/styles/layout';

body {
  // CSS variables
  // Colors
  --app-color-primary: #E23434;
  --app-color-accent: #333745;
  --app-color-text: #FFFFFF;
}
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
