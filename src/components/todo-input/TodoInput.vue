<template>
  <form class="form-inline">
    <div class="input-group mb-2 mr-sm-2">
      <!-- 输入框前缀 -->
      <div class="input-group-prepend">
        <div class="input-group-text">任务</div>
      </div>
      <!-- 文本输入框 -->
      <input type="text" class="form-control" placeholder="请填写任务信息" style="width: 356px" />
    </div>

    <!-- 添加按钮 -->
    <button type="submit" class="btn btn-primary mb-2">添加新任务</button>
  </form>
</template>

<script>
export default {
  name: 'TodoInput'
}
</script>

<style lang="less" scoped></style>
