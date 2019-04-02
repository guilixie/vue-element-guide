<template>
  <div>
    <el-table
      :data="data"
      v-loading="loading"
      :stripe="stripe"
      :border="border"
      :height="height"
      :max-height="maxHeight"
      :empty-text="emptyText"
      tooltip-effect="dark"
      @sort-change="handleSortChange"
      style="width: 100%">
      <el-table-column
        v-for="(item, idx) in headdata"
        show-overflow-tooltip
        :prop="item.prop"
        :label="item.label"
        :width="item.width"
        :min-width="item.minWidth"
        :key="`table_col_${idx}`"
        :sortable="item.sortable || false"
        />
    </el-table>
    <pagination style="padding:10px 0;text-align: right;" :total="pager.total" :current-page="pager.currentPage" :page-size="pager.pageSize" v-if="haspager" @getList="$emit('getList', $event)"/>
  </div>
</template>
<script>
import Pagination from './Pagination'
export default {
  name: 'TableView',
  components: {
    Pagination
  },
  props: {
    data: Array,
    loading: Boolean,
    stripe: Boolean,
    border: Boolean,
    height: [String, Number],
    maxHeight: [String, Number],
    emptyText: String,
    headdata: Array,
    haspager: Boolean,
    pager: Object
  },
  methods: {
    /* 排序处理 */
    handleSortChange ({column, prop, order}) {
      this.$emit('sortChange', {column, prop, order})
    }
  }
}
</script>
