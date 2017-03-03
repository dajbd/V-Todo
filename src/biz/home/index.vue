<template>
  <div class="page-home">
    <div class="header">
      <h1>V-Todo</h1>
    </div>

    <div class="body">
      <div class="list-wrapper">
        <h2>待办列表</h2>
        <ul>
          <li v-for="item in todoList">{{ item.title }}</li>
        </ul>
      </div>

      <div class="list-wrapper">
        <h2>已完成列表</h2>
        <ul>
          <li v-for="item in completedList">{{ item.title }}</li>
        </ul>
      </div>

    </div>

    <div class="footer">
      <form @submit.prevent>
        <input type="text" placeholder="准备做什么？"
          v-model="input"
          @keyup.enter="handleSubmit">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      todoList: [],
      completedList: [],
      input: ''
    }
  },
  methods: {
    handleSubmit () {
      let v = this.input.trim()
      if (v) {
        this.todoList.unshift({
          title: v
        })
        this.input = ''
      }
    }
  }
}
</script>

<style>
  .page-home {
    .header {
      h1 {
        font-size: 16px;
      }
    }
  }
</style>
