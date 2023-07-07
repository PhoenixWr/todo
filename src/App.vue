<template>
  <div>
    <h1>App.vue根组件</h1>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      // 任务列表数据
      todolist: [
        { id: 1, task: '周一早晨9点开会', done: false },
        { id: 2, task: '周一晚上8点聚餐', done: false },
        { id: 3, task: '准备周三上午的演讲稿', done: true }
      ]
    }
  }
}
</script>

<style lang="less" scoped></style>
