<template>
  <div class="home">
    <WallBg />
    <HelloWorld msg="建设中...:)"/>
    <Cat/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Cat from '@/components/Cat.vue'
import WallBg from '@/components/WallBg.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    Cat,
    WallBg
  }
}
</script>
<style scoped lang="scss">

</style>
