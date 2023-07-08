<template>
  <div>
    <h1>App 根组件</h1>

    <TodoList :list="todolist"></TodoList>
  </div>
</template>

<script>
// 导入需要注册的组件
import TodoList from '@/components/todo-list/TodoList.vue'

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
  },
  // 注册局部组件
  components: {
    TodoList
  }
}
</script>

<style lang="less" scoped></style>
