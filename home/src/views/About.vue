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
            if (r === 0 && g === 0 && b === 0) {
              arr[i][j] = '#0'// 上墙 00
            } else if (r === 34 && g === 32 && b === 52) {
              arr[i][j] = '#1'// 下墙 01
            } else if (r === 69 && g === 40 && b === 60) {
              arr[i][j] = '#2'// 左墙 02
            } else if (r === 102 && g === 57 && b === 49) {
              arr[i][j] = '#3'// 右墙 03
            } else if (r === 143 && g === 86 && b === 59) {
              arr[i][j] = '#4'// 左上角 10
            } else if (r === 223 && g === 113 && b === 38) {
              arr[i][j] = '#5'// 右上角 11
            } else if (r === 217 && g === 160 && b === 102) {
              arr[i][j] = '#6'// 左下角 12
            } else if (r === 238 && g === 195 && b === 154) {
              arr[i][j] = '#7'// 右下角 13
            } else if (r === 75 && g === 105 && b === 47) {
              arr[i][j] = '#8'// 非边界墙体 50
            } else if (r === 82 && g === 75 && b === 36) {
              arr[i][j] = '##'// 非边界矮墙 51
            } else if (r === 251 && g === 242 && b === 54) {
              arr[i][j] = 'P0'// 上门 20
            } else if (r === 153 && g === 229 && b === 80) {
              arr[i][j] = 'P1'// 下门 21
            } else if (r === 106 && g === 190 && b === 48) {
              arr[i][j] = 'P2'// 左门 22
            } else if (r === 55 && g === 148 && b === 110) {
              arr[i][j] = 'P3'// 右门 23
            } else if (r === 217 && g === 87 && b === 99) {
              arr[i][j] = 'E0'// 入口 70
            } else if (r === 215 && g === 123 && b === 186) {
              arr[i][j] = 'E1'// 出口 71
            } else if (r === 105 && g === 106 && b === 106) {
              arr[i][j] = '**'// 地板 60
            } else if (r === 89 && g === 86 && b === 82) {
              arr[i][j] = '*4'// 地板覆盖物 61
            } else if (r === 143 && g === 151 && b === 74) {
              arr[i][j] = '#S'// 开始标志 72
            } else if (r === 138 && g === 111 && b === 48) {
              arr[i][j] = '#E'// 结束标志 73
            } else if (r === 48 && g === 96 && b === 130) {
              arr[i][j] = 'C0'// 宝箱 40
            } else if (r === 91 && g === 110 && b === 225) {
              arr[i][j] = '~~'// 水 41
            } else if (r === 99 && g === 155 && b === 255) {
              arr[i][j] = '~0'// 水边 42
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
