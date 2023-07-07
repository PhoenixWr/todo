<template>
  <ul class="list-group">
    <!-- 列表项 -->
    <li class="list-group-item d-flex justify-content-between align-items-center">
      <!-- 复选框 -->
      <div class="form-check">
        <input class="form-check-input" type="checkbox" value="" id="defaultCheck1" />
        <label class="form-check-label" for="defaultCheck1"> Default checkbox </label>
      </div>
      <!-- 徽标 -->
      <span class="badge badge-success badge-pill">完成</span>
      <span class="badge badge-warning badge-pill">未完成</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TodoList'
}
</script>

<style lang="less" scoped></style>
