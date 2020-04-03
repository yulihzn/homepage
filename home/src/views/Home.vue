<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <WallBg />
    <HelloWorld msg="建设中...:)"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import WallBg from '@/components/WallBg.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    WallBg
  }
}
</script>
<style scoped lang="scss">

</style>
