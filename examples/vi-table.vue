<!--
 * @Author: huanghui
 * @Date: 2020-05-27 09:47:17
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2020-05-29 16:22:21
 * @FilePath: /backend-system-comp/examples/vi-table.vue
--> 
<template>
  <vi-table
    :data="tableData"
    :stripe="true"
    :pagination="paginationConfig"
  >
    <el-table-column
      prop="date"
      label="日期"
      width="180">
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      width="180">
    </el-table-column>
    <el-table-column
      prop="address"
      label="地址">
    </el-table-column>
  </vi-table>
</template>

<script>
/** 
 * 带分页的table
 * */
import ViTable from '@/components/vi-table.vue'
export default {
  components: {
    ViTable
  },
  data () {
    return {
      paginationConfig: {
        'page-sizes': [20, 30, 40],
        'layout': "total, sizes, prev, pager, next, jumper",
        'current-page': 1,
        'total': 120,
        'current-change': (val) => {
          console.log(val, 'current')
        },
        'prev-click': (val) => {
          console.log(val, 'prev')
        }
      },
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄'
      }, {
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄'
      }]
    }
  }
}
</script>

