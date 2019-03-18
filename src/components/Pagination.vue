<template>
	<el-pagination
		background
		@size-change="handleSizeChange"
		@current-change="handleCurrentChange"
		:current-page="currentPage"
		:page-sizes="pageSizes"
		:page-size="pageSize"
		layout="total, sizes, prev, pager, next, jumper"
		:total="total"
		:prev-text="prevText"
		:next-text="nextText"
		v-if="total"
	>
	</el-pagination>
</template>
<script>
export default {
	name: 'Pagination',
	props: {
		prevText: String,
		nextText: String,
		total: {
			type: Number,
			default: 0
		},
		currentPage: {
			type: Number,
			default: 1
		},
		pageSize: {
			type: Number,
			default: 10
		},
		pageSizes: {
			type: Array,
			default() {
				return [5, 10, 15, 20, 25, 30, 50, 80, 100]
			}
		}
	},
	methods: {
		handleSizeChange(val) {
			this.$emit('getList', {
				currentPage: 1,
				pageSize: val
			})
		},
		handleCurrentChange(val) {
			this.$emit('getList', {
				currentPage: val,
				pageSize: this.pageSize
			})
		}
	}
}
</script>
