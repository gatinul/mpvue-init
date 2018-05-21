<template lang="html">
  <div class="">
    <div class="modal-mask" catchtouchmove="preventTouchMove" v-if="showModal"></div>
    <div class="modal-dialog" v-if="showModal">
      <div class="modal-title">{{title}}</div>
      <div class="modal-content">
        <div class="modal-input">
          <slot></slot>
        </div>
      </div>
      <div class="modal-footer">
        <div v-if="cannelText" class="btn-cancel" @click="selfCannel" data-status="cancel">{{cannelText}}</div>
        <div v-if="okText" class="btn-confirm" @click="selfOk" data-status="confirm">{{okText}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['showModal', 'title', 'cannelText', 'okText'],
  methods: {
    selfCannel () {
      this.$emit('modalCannel')
    },
    selfOk () {
      this.$emit('modalOk')
    }
  }
}
</script>

<style>
.show-btn {
margin-top: 100rpx;
color: #22cc22;
}

.modal-mask {
width: 100%;
height: 100%;
position: fixed;
top: 0;
left: 0;
background: #000;
opacity: 0.5;
overflow: hidden;
z-index: 9000;
color: #fff;
}

.modal-dialog {
width: 540rpx;
overflow: hidden;
position: absolute;
top: 18%;
left: 15%;
z-index: 9999;
background: #fff;
border-radius: 18rpx;
}

.modal-title {
padding-top: 50rpx;
font-size: 36rpx;
color: #030303;
text-align: center;
}

.modal-content {
padding: 50rpx 32rpx;
}

.modal-input {
display: flex;
border-radius: 4rpx;
font-size: 28rpx;
}


.input {
width: 100%;
height: 82rpx;
font-size: 28rpx;
line-height: 28rpx;
padding: 0 20rpx;
box-sizing: border-box;
color: #333;
}

input-holder {
color: #666;
font-size: 28rpx;
}

.modal-footer {
display: flex;
flex-direction: row;
height: 86rpx;
border-top: 1px solid #dedede;
font-size: 34rpx;
line-height: 86rpx;
}

.btn-cancel {
width: 50%;
color: #666;
text-align: center;
border-right: 1px solid #dedede;
}

.btn-confirm {
width: 50%;
color: #ec5300;
text-align: center;
}
</style>
