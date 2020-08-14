<template>
  <div class="main-container">
    <img alt="Vue logo" :src='src' width="58" height="34" @click="pickUpCat()" >
  </div>
</template>

<script>
export default {
  name: 'Cat',
  props: {
  },
  data () {
    return {
      src: '',
      currentRes: 'assets/cat/cat_idle_000.png'
    }
  },
  created () {
    this.src = require('@/' + this.currentRes)
  },
  mounted () {},
  methods: {
    pickUpCat () {
      console.log('picked me')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

a {
  color: #42b983;
}
.game {
  display: inline;
  position: relative;
  margin: 32px;
}
.wine {
  display: inline;
  position: relative;
  margin: 32px;
}

.main-container {
  position: fixed;
  display: flex;
  top: 8%;
  height: 100%;
  width: 100%;
  justify-content: center;
}
</style>
