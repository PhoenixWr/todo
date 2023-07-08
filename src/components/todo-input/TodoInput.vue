<template>
  <form class="form-inline" @submit.prevent="onFormSubmit">
    <div class="input-group mb-2 mr-sm-2">
      <!-- 输入框前缀 -->
      <div class="input-group-prepend">
        <div class="input-group-text">任务</div>
      </div>
      <!-- 文本输入框 -->
      <input type="text" class="form-control" placeholder="请填写任务信息" style="width: 356px" v-model.trim="taskname" @keyup.esc="taskname = ''" />
    </div>

    <!-- 添加按钮 -->
    <button type="submit" class="btn btn-primary mb-2">添加新任务</button>
  </form>
</template>

<script>
export default {
  name: 'TodoInput',
  // 声明自定义事件
  emits: ['addTask'],
  data() {
    return {
      // 新任务名称
      taskname: ''
    }
  },
  methods: {
    // 表单提交事件处理函数
    onFormSubmit() {
      // 非空验证
      if (!this.taskname) return alert('任务名称不允许为空')
      // 触发自定义事件，向外部传递任务名称数据
      this.$emit('addTask', this.taskname)
      // 清空文本框
      this.taskname = ''
    }
  }
}
</script>

<style lang="less" scoped></style>
