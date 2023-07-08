<template>
  <div>
    <h1>App 根组件</h1>
    <hr />

    <TodoInput @add-task="onAddTask"></TodoInput>
    <TodoList :list="tasklist"></TodoList>
    <TodoButton v-model:active="activeIndex"></TodoButton>
  </div>
</template>

<script>
// 导入需要注册的组件
import TodoList from '@/components/todo-list/TodoList.vue'
import TodoInput from '@/components/todo-input/TodoInput.vue'
import TodoButton from '@/components/todo-button/TodoButton.vue'

export default {
  name: 'App',
  // 注册局部组件
  components: {
    TodoList,
    TodoInput,
    TodoButton
  },
  computed: {
    // 添加新任务的id
    nextId() {
      const length = this.todolist.length
      return length ? this.todolist[length - 1].id + 1 : 1
    },
    // 根据激活按钮索引值动态计算要展示的任务列表数据
    tasklist() {
      switch (this.activeIndex) {
        case 0: // 全部
          return this.todolist
        case 1: // 已完成
          return this.todolist.filter(item => item.done)
        case 2: // 未完成
          return this.todolist.filter(item => !item.done)
      }
    }
  },
  data() {
    return {
      // 任务列表数据
      todolist: [
        { id: 1, task: '周一早晨9点开会', done: false },
        { id: 2, task: '周一晚上8点聚餐', done: false },
        { id: 3, task: '准备周三上午的演讲稿', done: true }
      ],
      // TodoButton默认激活项索引
      activeIndex: 0
    }
  },
  methods: {
    // TodoInput组件自定义事件add-task处理函数
    onAddTask(taskname) {
      // 向任务列表中添加新任务数据
      this.todolist.push({
        id: this.nextId,
        task: taskname,
        done: false
      })
    }
  }
}
</script>

<style lang="less" scoped></style>
