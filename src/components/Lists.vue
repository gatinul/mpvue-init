<template lang="html">
  <div class="ui list_content list_appmsg" @click="selfClick(imgPath, content)">
      <div v-if="imgPath" class="ui list_left">
          <image class="ui list_img" :src="imgPath" />
      </div>
      <div class="ui list_right">
          <div v-for="(item, index) in content" :key="index" class="ui list_desc">{{item}}</div>
      </div>
  </div>
</template>

<script>
export default {
  props: ['imgPath', 'content'],
  methods: {
    selfClick (imgPath, content) {
      if (imgPath) {
        this.$emit('itemClick', imgPath, content)
      } else {
        this.$emit('itemClick', content)
      }
    }
  }
}
</script>

<style lang="css">
</style>
