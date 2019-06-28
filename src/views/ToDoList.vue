<template>
  <div>
    <h1>Learn Vuex 2.0 Todo List</h1>
    <input type="text" placeholder="add Todo.." />
    <input type="submit" value="新增" @click="addToList()"/>
    <div class="center-inline">
      <div>
        <h3 class="list-title">Todo List</h3>
        <ul>
          <li v-for="todo in todo_list" :key="todo.id" class="list-item">
            <input type="checkbox" :name="todo" :id="key" /> {{ todo.title }}
            <button>修改</button>
            <input type="button" value="刪除" />
          </li>
        </ul>
      </div>
      <div>
        <h3>Done List</h3>
        <ul>
          <li v-for="done in done_list" :key="done.id">
            <input type="checkbox" :id="key" />
            {{ done.title }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    todo_list: [
      { title: 'Vue.js 2.0' },
      { title: 'Vuex 2.0' },
      { title: 'Webpack 2.0' }
    ],
    done_list: [{ title: 'Vue-router 2.0' }]
  }),
  methods: {
    
  }
}
</script>

<style>
.center-inline {
  margin: 0px auto;
}

.center-inline div {
  display: inline-block;
  vertical-align: top;
  width: 300px;
}

.list-title {
  padding-left: 20px;
  text-align: left;
}

.list-item {
  text-align: left;
}
</style>
