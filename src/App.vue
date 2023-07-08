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
  watch: {
    // 深度侦听todolist数组中数据变化，将更新后的数据同步存储到本地存储
    todolist: {
      handler(newValue) {
        localStorage.setItem('todolist', JSON.stringify(newValue))
      },
      // 复杂数据类型需要开启深度侦听，侦听数组或对象内部数据变化
      deep: true
    }
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
      todolist: JSON.parse(localStorage.getItem('todolist')) || [],
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
