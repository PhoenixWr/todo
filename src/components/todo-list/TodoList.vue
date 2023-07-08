<template>
  <ul class="list-group overflow-auto mt-2">
    <!-- 列表项 -->
    <li class="list-group-item d-flex justify-content-between align-items-center" v-for="item in list" :key="item.id">
      <!-- 复选框 -->
      <div class="form-check">
        <input class="form-check-input" type="checkbox" value="" :id="item.id" v-model="item.done" />
        <label class="form-check-label" :class="item.done ? 'delete' : ''" :for="item.id">{{ item.task }}</label>
      </div>
      <!-- 徽标 -->
      <span class="badge badge-success badge-pill" v-if="item.done">完成</span>
      <span class="badge badge-warning badge-pill" v-else>未完成</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    // 任务列表数据
    list: {
      type: Array,
      required: true,
      default: []
    }
  }
}
</script>

<style lang="less" scoped>
// 调整列表组宽度
.list-group {
  width: 400px;
  height: 150px;
}

// 删除效果
.delete {
  text-decoration: line-through;
  font-style: italic;
  color: gray;
}
</style>
