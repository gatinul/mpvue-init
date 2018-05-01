<template lang="html">
    <div v-if="text" style="padding-bottom:.2rem">
      <div class="ui badge" style="margin-left: 5px;">{{text}}</div>
    </div>
    <div v-else>
      <div class="" style="font-size: 0">
        <div style="display: inline-block;vertical-align:middle; font-size: 17px;"></div>
        <div class="ui badge badge_dot" style="margin-left: 5px;margin-right: 5px;"></div>
      </div>
    </div>
</template>

<script>
export default {
  props: ['text']
}
</script>

<style lang="css">
</style>
