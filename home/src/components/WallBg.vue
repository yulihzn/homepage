<template>
  <div class="main-container">
      <div class="wall-bg-border"></div>
    <div class="wall-bg-top">
      <div class="window-table">
      <div class="window-table-bg"></div>
        <table class="window-table-frame" border="2">
        <tr><td></td><td></td><td></td></tr>
        <tr><td></td><td></td><td></td></tr>
        <tr><td></td><td></td><td></td></tr>
      </table>
      </div>
    </div>
    <div class="wall-bg-border"></div>
    <div class="wall-bg-bottom"></div>
  </div>
</template>

<script>
export default {
  name: 'WallBg',
  props: {},
  data () {
    return {}
  },
  mounted () {}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main-container {
  height: 100%;
  width: 100%;
  justify-content: center;
}
.wall-bg-bottom {
  background: rgb(212, 250, 248);
  width: 100%;
  height: 200px;
}
.wall-bg-border {
  width: 100%;
  background: ghostwhite;
  border: 2px solid gainsboro;
  height: 20px;
}
.wall-bg-top {
  width: 100%;
  background: ghostwhite;
  display: flex;
  height: 300px;
}
.window-table {
  margin: 0 auto;
  position: relative;
  width: 300px;
  height: 300px;
  border:gainsboro;
}
.window-table-bg {
  width: 300px;
  height: 300px;
  position: absolute;
  background: rgb(215, 236, 255);
}
.window-table-frame {
  width: 300px;
  height: 300px;
  position: absolute;
}
</style>
