<template>
  <div class="tubiao">
<el-tabs v-model="activeName"  @tab-click="handleClick">
    <el-tab-pane label="部门业绩图" name="first"></el-tab-pane>
 </el-tabs>
  <echart />
</div>
</template>
<script>
import Echart from '@/components/TwoEcharts'
export default {
  name: 'Charts',
  data () {
    return {
      dataAll: {},
      typeBoolean: true,
      date: ''
    }
  },
  computed: {
    type: function () {
      return this.typeBoolean ? 'bar' : 'line'
    }
  },
  components: {
    Echart
  }
}
</script>
<style scoped lang="scss">
.filter-charts {
  border: 1px solid rgba(155, 155, 155, 0.2)
}
</style>
