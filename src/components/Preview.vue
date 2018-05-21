<template lang="html">
  <div class="ui preview">
      <div class="ui preview_hd">
          <div class="ui preview_hd_label">{{title.label}}</div>
          <div class="ui preview_value_in-hd">{{title.text}}</div>
      </div>
      <div class="ui preview_bd">
          <div class="ui preview_item" v-for="(item, index) in content" :key="index">
              <div class="ui preview_label">{{item.label}}</div>
              <div class="ui preview_value">{{item.text}}</div>
          </div>
      </div>
      <div class="ui preview_ft">
          <div v-if="cannelText" @click="selfCannel(content, title)" :class="cannelStyle" class="ui preview_btn preview_btn_red">{{cannelText}}</div>
          <div v-if="sureText" @click="selfSure(content, title)" :class="sureStyle" class="ui preview_btn preview_btn_primary">{{sureText}}</div>
      </div>
  </div>
</template>

<script>
export default {
  props: ['title', 'content', 'cannelText', 'sureText', 'cannelStyle', 'sureStyle'],
  methods: {
    selfCannel (content, title) {
      this.$emit('cannel', content, title)
    },
    selfSure (content, title) {
      this.$emit('sure', content, title)
    }
  }
}
</script>

<style lang="css">
</style>
