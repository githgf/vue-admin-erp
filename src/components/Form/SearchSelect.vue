<template>
  <section class="p-10">
    <el-select v-model="value" :filter-method="dataFilter" placeholder="请选择" filterable >
      <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value" />
    </el-select>
  </section>
</template>

<script>
export default {
  // 带有搜索功能的下拉菜单
  name: 'SearchSelect',
  data() {
    return {
      optionsCopy: [{
        value: '1',
        label: 'meat'
      }, {
        value: '2',
        label: 'drink'
      }, {
        value: '3',
        label: 'food'
      }, {
        value: '4',
        label: '龙须面'
      }, {
        value: '5',
        label: '北京烤鸭'
      }],
      options: [{
        value: '1',
        label: 'meat'
      }, {
        value: '2',
        label: 'drink'
      }, {
        value: '3',
        label: 'food'
      }, {
        value: '4',
        label: '龙须面'
      }, {
        value: '5',
        label: '北京烤鸭'
      }],
      value: ''
    }
  },
  methods: {
    dataFilter(val) {
      this.value = val
      if (val) { // val存在
        this.options = this.optionsCopy.filter((item) => {
          if (!!~item.label.indexOf(val) || !!~item.label.toUpperCase().indexOf(val.toUpperCase())) {
            return true
          }
        })
      } else { // val为空时，还原数组
        this.options = this.optionsCopy
      }
    }
  }
}
</script>

<style scoped>

</style>
