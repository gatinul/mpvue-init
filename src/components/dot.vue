<template lang="html">
    <div v-if="text == point" class="components_dot_right">
      <div  style="font-size: 0">
        <div style="display: inline-block;vertical-align:middle; font-size: 17px;"></div>
        <div class="ui badge badge_dot" style="margin-left: 5px;margin-right: 5px;"></div>
      </div>
    </div>
    <div v-else style="padding-bottom:.2rem">
      <div class="ui badge" style="margin-left: 5px;">{{text}}</div>

    </div>
</template>

<script>
export default {
  props: ['text'],
  data () {
    return {
      point: 'point'
    }
  }
}
</script>

<style lang="css">
.components_dot_right{
  position: absolute;
  right: 30rpx;
}
</style>
