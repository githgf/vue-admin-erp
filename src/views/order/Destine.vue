<template>
  <el-collapse v-model="activeNames" @change="handleChange">
    <el-collapse-item name="1">
      <template slot="title">
        <h3 class="collapse-title">客户详情</h3>
      </template>
      <el-form
        ref="form"
        :model="clientForm"
        style="width: 100%">
        <el-form-item label="客户名称" style="margin-left: 10px">
          <SearchSelect/>
        </el-form-item>
        <el-form-item
          :rules="[
            { required: true, message: '电话不能为空'},
            { type: 'number', message: '号码必须为数字值'}
          ]"
          prop="clientTel"
          label="联系电话"
          style="margin-left: 10px;width: 40%">
          <el-input v-model.number="clientForm.clientTel"/>
        </el-form-item>
        <el-form-item
          :rules="[
            { required: true, message: '请输入家庭地址', trigger: 'blur' }
          ]"
          label="家庭地址"
          prop="address"
          style="width: 60%;margin-left: 10px">
          <el-input v-model="clientForm.address"/>
        </el-form-item>
      </el-form>
    </el-collapse-item>
    <el-collapse-item name="2">
      <template slot="title">
        <h3 class="collapse-title">订单详情</h3>
      </template>
      <el-table
        :data="tableData"
        border
        style="width: 100%">
        <el-table-column
          fixed
          prop="date"
          label="日期"
          width="150" />
        <el-table-column
          prop="name"
          label="姓名"
          width="120" />
        <el-table-column
          prop="province"
          label="省份"
          width="120"/>
        <el-table-column
          prop="city"
          label="市区"
          width="120"/>
        <el-table-column
          prop="address"
          label="地址"
          width="300"/>
        <el-table-column
          prop="zip"
          label="邮编"
          width="120"/>
        <el-table-column
          fixed="right"
          label="操作"
          width="100">
          <template slot-scope="scope">
            <el-button type="text" size="small" @click="handleClick(scope.row)" >查看</el-button>
            <el-button type="text" size="small">编辑</el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-collapse-item>
  </el-collapse>
</template>

<script>
import SearchSelect from '@/components/Form/SearchSelect'

export default {
  name: 'Destine',
  components: { SearchSelect },
  data() {
    return {
      clientForm: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        address: '',
        clientTel: ''
      },
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-04',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1517 弄',
        zip: 200333
      }, {
        date: '2016-05-01',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1519 弄',
        zip: 200333
      }, {
        date: '2016-05-03',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1516 弄',
        zip: 200333
      }],
      activeNames: ['1'],
      dialogFormVisible: false
    }
  },
  methods: {
    handleClick(row) {
      console.log(row)
    },
    handleChange(val) {
      console.log(val)
    }
  }
}
</script>

<style scoped>
.collapse-title{
  color: #409EFF;
  display: block;
  margin-left: 50%;
}

</style>
