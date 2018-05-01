<template lang="html">
  <div class="ui cells" :class="className">
      <div class="ui cell" v-for="(item, index) in dataSource" :key="index">
        <div>{{item.title}}</div>
        <div class="ui cell_in-access"></div>
        <dot v-if="item.dot" :text="item.dot"></dot>
      </div>
  </div>

</template>

<script>
import dot from '@/components/dot'

export default {
  props: ['dataSource', 'className'],
  components: {
    dot
  }
}
</script>

<style lang="css">
</style>
