<template lang="html">
  <!-- <div class="ui cells" :class="className">
      <div class="ui cell" v-for="(item, index) in dataSource" :key="index">
        <div>{{item.title}}</div>
        <div class="ui cell_in-access"></div>
        <Dot v-if="item.dot" :text="item.dot"></Dot>
      </div>
  </div> -->
  <div class="ui cell" @click="selfClick(title)">
    <div>{{title}}</div>
    <div v-if="link" class="ui cell_in-access"></div>
    <Dot v-if="dot" :text="dot"></Dot>
  </div>

</template>

<script>
import Dot from '@/components/Dot'

export default {
  props: ['title', 'dot', 'link'],
  components: {
    Dot
  },
  methods: {
    selfClick (title) {
      this.$emit('cellClick', title)
    }
  }
}
</script>

<style lang="css">
</style>
