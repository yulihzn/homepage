<template>
  <div class="main-container">
    <img alt="Vue logo" :src='src' width="96" height="96" @click="pickUpCat()" >
      <router-link to="/about"><img src="@/assets/cat/plant.png" ></router-link>
      <a href="http://banditcatstudio.com/web-mobile"><img src="@/assets/avatarbed.png" ></a>
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
      currentRes: 'assets/cat/cat_idle_000.png',
      isAniming: false
    }
  },
  created () {
    this.src = require('@/' + this.currentRes)
  },
  mounted () {},
  methods: {
    pickUpCat () {
      console.log('picked me')
      if (this.isAniming) {
        return
      }
      let arr = [0, 1, 2, 3, 4, 5, 4, 3, 2, 1, 0]
      let index = 0
      this.isAniming = true
      let interval = setInterval(() => {
        if (index > arr.length - 1) {
          clearInterval(interval)
          this.isAniming = false
          return
        }
        this.src = require('@/' + `assets/cat/cat_picked_00${arr[index++]}.png`)
      }, 100)
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
  top: 80%;
  left: 30%;
  height: 100%;
  width: 100%;
  justify-content: center;
  justify-items: center;
}
</style>
