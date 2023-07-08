<template>
  <div class="todobutton-container mt-3">
    <div class="btn-group">
      <button type="button" class="btn" :class="active === 0 ? 'btn-primary' : 'btn-secondary'" @click="updateActive(0)">全部</button>
      <button type="button" class="btn" :class="active === 1 ? 'btn-primary' : 'btn-secondary'" @click="updateActive(1)">已完成</button>
      <button type="button" class="btn" :class="active === 2 ? 'btn-primary' : 'btn-secondary'" @click="updateActive(2)">未完成</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoButton',
  emits: ['update:active'],
  props: {
    // 激活项索引值
    // 0: 全部 1: 已完成 2: 未完成
    active: {
      type: Number,
      required: true,
      default: 0
    }
  },
  methods: {
    updateActive(index) {
      // 判断触发点击事件的按钮激活项索引是否和当前props中激活项索引一致
      // 索引一致则没有必要触发事件进行active更新
      if (index === this.active) return
      // 触发自定义事件更新父组件中 activeIndex 的值
      this.$emit('update:active', index)
    }
  }
}
</script>

<style lang="less" scoped>
.todobutton-container {
  width: 400px;
  text-align: center;
}
</style>
