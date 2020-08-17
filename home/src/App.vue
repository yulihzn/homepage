<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">首页</router-link>
    </div>
      <!-- <router-link to="/about">About</router-link> -->
    <router-view/>
  </div>
</template>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 10px;
  a {
    font-weight: bold;
    color: #080808;
    &.router-link-exact-active {
      color: #626e69;
    }
  }
}
</style>
