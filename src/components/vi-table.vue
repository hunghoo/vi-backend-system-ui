<template>
  <div class="vi-table-wrapper">
    <el-table
      :data="data"
      v-bind="$attrs"
      v-on="$listeners"
      border>
      <slot></slot>
    </el-table>
    <el-pagination
      class="vi-table-pagination"
      :class="paginationClass"
      v-bind="paginationConfig"
      v-on="paginationEvents"
    >
    </el-pagination>
  </div>
</template>
<script>
// 跳页配置项
const paginationConfig = {
  'page-sizes': [5, 10, 20, 30, 40],
  'layout': "total, sizes, prev, pager, next, jumper",
  'current-page': 1,
  'total': 0
}
const nullFn = () => {}
export default {
  props: {
    data: {
      type: Array
    },
    pagination: {
      type: Object
    }
  },
  data () {
    return {
      paginationConfig: {
        ...paginationConfig,
        'small': this.pagination['small'],
        'background': this.pagination['background'],
        'page-size': this.pagination['page-size'],
        'total': this.pagination['total'],
        'page-count': this.pagination['page-count'],
        'pager-count': this.pagination['pager-count'],
        'current-page': this.pagination['current-page'],
        'layout': this.pagination['layout'],
        'page-sizes': this.pagination['page-sizes'],
        'popper-class': this.pagination['popper-class'],
        'prev-text': this.pagination['prev-text'],
        'next-text': this.pagination['next-text'],
        'disabled': this.pagination['disabled'],
        'hide-on-single-page': this.pagination['hide-on-single-page']
      },
      paginationEvents: {
        'size-change': this.pagination['size-change'] || nullFn,
        'current-change': this.pagination['current-change'] || nullFn,
        'prev-click': this.pagination['prev-click'] || nullFn,
        'next-click': this.pagination['next-click'] || nullFn
      },
      paginationClass: this.pagination.positon || 'right'
    }
  }
}
</script>
<style>
.vi-table-pagination {
  display: flex;
  height: 40px;
  align-items: center;
}
.vi-table-pagination.center {
  justify-content: center;
}
.vi-table-pagination.left {
  justify-content: flex-start;
}
.vi-table-pagination.right {
  justify-content: flex-end;
}
</style>
