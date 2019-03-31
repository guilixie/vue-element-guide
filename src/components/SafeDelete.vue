<template>
  <el-popover
    placement="top"
    width="200"
    v-model="visible">
    <p>{{text}}</p>
    <div style="text-align: right; margin: 0">
      <el-button size="mini" type="text" @click="visible = false">取消</el-button>
      <el-button type="primary" size="mini" @click="[visible = false, confirm()]">确定</el-button>
    </div>
    <el-button :size="size || 'mini'" :plain="plain" type="danger" slot="reference"><slot></slot></el-button>
  </el-popover>
</template>
<script>
export default {
  name: 'SafeDelete',
  props: {
    text: String,
    size: String,
    plain: Boolean,
    scope: Object
  },
  data () {
    return {
      visible: false
    }
  },
  methods: {
    confirm () {
      this.$emit('confirm', this.scope)
    }
  }
}
</script>
