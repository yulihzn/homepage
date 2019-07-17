<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <a class="game" href="https://banditcatstudio.com/web-mobile/index.html"><img src=".././assets/gamepad.png"/></a>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.game{
  position: fixed;
  bottom: 32px;
}
</style>
