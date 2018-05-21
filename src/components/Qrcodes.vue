<template lang="html">
  <div class="" style="margin:5px auto">
    <!-- <div class="container-box">
      <image style="width:150px;height:130px" :src="imgPath" ></image>
    </div> -->
    <div v-if="maskShow" class="mask"></div>
    <div class="canvas-box">
      <canvas style="width:150px" canvas-id="mycanvas"/>
    </div>
  </div>
</template>

<script>
import QR from  '../utils/qrcode'
export default {
  props: ['content', 'width', 'height'],
  data () {
    return {
      imgShow: false,
      maskShow: false,
      imgPath: ''
    }
  },
  onLoad () {
    const self = this;
    self.maskShow = true
    // const url = 'http://broad.10010lt.com/chbb/e10010/online/index.do?ID=20180309130005082820'
    const url = self.content
    wx.showToast({
      title: '生成中...',
      icon: 'loading',
      duration:500
    });
    const st = setTimeout(function(){
      wx.hideToast()
      // const size = self.setCanvasSize()

      const size = self.setSize()
      //绘制二维码
      self.createQrCode(url, "mycanvas", size.w, size.h)
      self.maskShow = false
      clearTimeout(st)
    },500)
  },
  methods: {
    // 适配不同屏幕大小的canvas
    setCanvasSize: function () {
      const self = this;
      const size={};
      try {
          const res = wx.getSystemInfoSync()
          const scale = 750/686//不同屏幕下canvas的适配比例；设计稿是750宽
          const width = res.windowWidth/scale
          const height = width//canvas画布为正方形
          size.w = width
          size.h = height
        } catch (e) {
          // Do something when catch error
          console.log("获取设备信息失败"+e)
        }
      return size
    },
    setSize: function () {
      const size = {}
      const width = this.width ? this.width : '150'
      const height = this.height ? this.width : '150'
      size.w = width
      size.h = height
      return size
    },
    createQrCode:function (url, canvasId, cavW, cavH) {
      // 调用插件中的draw方法，绘制二维码图片
      QR.draw(url, canvasId, cavW, cavH, this)
      setTimeout(() => {
        this.canvasToTempImage()
      }, 1000)
    },
    // 获取临时缓存照片路径，存入data中
    canvasToTempImage: function () {
      const self = this
      wx.canvasToTempFilePath({
        canvasId: 'mycanvas',
        success: function (res) {
          const tempFilePath = res.tempFilePath
          console.log(tempFilePath)
          self.imgPath = tempFilePath
          self.imgShow = true;
        },
        fail: function (res) {
          console.log(res)
        }
      })
    }
  }
}
</script>

<style lang="css">
</style>
