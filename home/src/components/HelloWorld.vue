<template>
  <div class="main-container">
    <h1 class="h3">{{ msg }}</h1>
    <div class="bottom-container">
    <a class="game" href="https://banditcatstudio.com/web-mobile/index.html"><img src=".././assets/gamepad.png"/></a>
    <a class="wine" href="https://banditcatstudio.com/dist/index.html"><img src=".././assets/wine.png"/></a>
    </div>
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
  position: relative;
  top: 50%;
  height: 100%;
  align-content: center;
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
  display: inline;
  position: relative;
  margin: 32px;
}
.wine{
  display: inline;
  position: relative;
  margin: 32px;
}
.bottom-container{
  position: fixed;
  display: flex;
  width: 100%;
  justify-content: center;
  bottom: 32px;
}
.main-container{
  position: fixed;
  display: flex;
  top: 30%;
  height: 100%;
  width: 100%;
  justify-content: center;
}
</style>
