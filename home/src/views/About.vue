<template>
  <div class="main-container">
    <input class="input-button" type="file" @change="fileChange" accept="image/png">
    <canvas id="canvas" v-clipboard:copy="mapStr" v-clipboard:success="getMapStr"/>
    <font id="text" class="input-text">{{mapStr}}</font>

  </div>
</template>
<script>

export default {
  name: 'About',
  props: {
  },
  data () {
    return {
      base64Img: [],
      mapStr: ''
    }
  },
  created () {
  },
  mounted () {},
  methods: {
    getMapStr () {
      alert('复制成功')
    },
    fileChange (e) {
      let file = e.target.files[0]
      let reader = new FileReader()
      reader.onload = value => {
        this.base64Img = []
        this.base64Img.push(value.target.result)
        let image = new Image()
        image.src = value.target.result
        // 延迟一下获取宽高
        setTimeout(() => {
          console.log(`width:${image.width} height:${image.height}`)
          this.showMap(image)
        }, 1)
      }
      reader.readAsDataURL(file)
    },
    showMap (image) {
      let width = image.width
      let height = image.height
      let canvas = document.getElementById('canvas')
      canvas.width = width
      canvas.height = height
      let ctx = canvas.getContext('2d')
      ctx.drawImage(image, 0, 0, width, height)
      let arr = []
      for (let i = 0; i < width; i++) {
        arr[i] = []
        for (let j = 0; j < height; j++) {
          let data = ctx.getImageData(i, j, 1, 1)
          let r = data.data[0]
          let g = data.data[1]
          let b = data.data[2]
          let a = data.data[3]
          if (a === 0) {
            arr[i][j] = '--'
          } else {
            arr[i][j] = `${(r + g + b) === 0 ? '#0' : '**'}`
            if (r === 255 && g === 0 && b === 0) {
              arr[i][j] = 'E0'
            } else if (r === 0 && g === 255 && b === 0) {
              arr[i][j] = 'D0'
            } else if (r === 0 && g === 0 && b === 255) {
              arr[i][j] = 'E1'
            }
          }
        }
      }
      let str = '\n'
      for (let j = 0; j < arr[0].length; j++) {
        for (let i = 0; i < arr.length; i++) {
          str += arr[i][j]
        }
        str += '\n'
      }
      this.mapStr = str
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main-container {
  position:fixed;
  display:list-item;
  justify-content: center;
  width: 100%;
  height: 100%;
  overflow: scroll;
}
.input-text{
  font-size: 4pt;
  font-family: monospace;
  white-space: pre;
}
.input-button{
  height: 24px;
}
</style>
