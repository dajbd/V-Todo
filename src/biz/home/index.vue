<template>
  <div class="page-home">
    <div class="header">
      <h1 class="head">V-Todo</h1>
    </div>

    <div class="body">
      <div class="list-wrapper">
        <h2 class="list-head"><span class="text">待办列表</span></h2>
        <ul class="list">
          <li class="item"
            v-for="item in todoList">{{ item.title }}</li>
        </ul>
      </div>

      <div class="list-wrapper">
        <h2 class="list-head"><span class="text">已完成列表</span></h2>
        <ul class="list">
          <li class="item"
            v-for="item in completedList">{{ item.title }}</li>
        </ul>
      </div>

    </div>

    <div class="footer">
      <form class="form" @submit.prevent>
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

<style lang="less">
  .page-home {
    height: 100%;
    overflow: hidden;
    .body {
      height: 100%;
      padding-top: 40px + 54px;
      margin-top: -40px - 54px;
      // background: #f2f2f2;
    }
    .header {
      position: relative;
      z-index: 10;
      background: #617FDE;
      color: #fff;
      .head {
        // 总高度计算为 40px
        padding: 12px 1em;
        font-size: 16px;
        line-height: 1em;
        text-align: center;
      }
    }

    .list-head {
      color: #666;
      background: #EBEFFC;
      .text {
        padding-top: 0.42em;
        padding-bottom: 0.42em;
        display: inline-block;
        font-size: 12px;
      }
    }

    .list-head,
    .list {
      padding-left: 1em;
      padding-right: 1em;
      min-height: 20px;
    }

    .list {
      .item {
        padding: 4px 0px 4px 0px;
        &:first-child {
          padding-top: 8px;
        }
        &:last-child {
          padding-bottom: 8px;
        }
      }
    }

    .footer {
      background: #F0F2F3;
      .form {
        padding: 9px 1em;
      }
      input {
        width: 100%;
        height: 36px;
        font-size: 14px;
        display: block;
        border-radius: 4px;
        border-color: #ccc;
      }
    }
  }
</style>
