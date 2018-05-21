<template lang="html">
  <div class="ui cell input">
      <div class="">
          <div class="ui label">{{ label }}</div>
      </div>
      <div class="">
          <input class="ui input" :placeholder="placeholder" :disabled="disabled" :type="type"
          :password="password" :value="value" :maxlength="max ? max :'140'" @input="selfChange"   />
      </div>
  </div>
</template>

<script>
export default {
  props: ['label', 'placeholder', 'disabled', 'type', 'password', 'max', 'value'],
  methods: {
    selfChange (e) {
      this.$emit('inputChange', e.target.value)
    }
  }
}
</script>

<style lang="css">
</style>
