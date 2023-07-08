<template>
  <div class="todobutton-container mt-3">
    <div class="btn-group">
      <button type="button" class="btn btn-primary">全部</button>
      <button type="button" class="btn btn-secondary">已完成</button>
      <button type="button" class="btn btn-secondary">未完成</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoButton'
}
</script>

<style lang="less" scoped>
.todobutton-container {
  width: 400px;
  text-align: center;
}
</style>
