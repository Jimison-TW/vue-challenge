<template>
  <div>
    <h1>Learn Vuex 2.0 Todo List</h1>
    <input type="text" placeholder="add Todo.." v-model="todo_value" />
    <input type="submit" value="新增" @click="addToList(todo_value)" />
    <div class="center-inline">
      <div>
        <h3 class="list-title">Todo List</h3>
        <ul>
          <li v-for="(todo, index) in todo_list" :key="todo.id" class="list-item">
            <input type="checkbox" v-model="todo.value" @change="checkFinished(index, todo.value)" />
            <span :hidden="todo.inEdit">{{ todo.title }}</span>
            <input type="text" v-model="todo.title" :hidden="!todo.inEdit" size="15"/>
            <button @click="editTodo(index)">修改</button>
            <input type="button" value="刪除" @click="removeTodo(index)" />
          </li>
        </ul>
      </div>
      <div>
        <h3 class="list-title">Done List</h3>
        <ul>
          <li v-for="done in done_list" :key="done.id" class="list-item">
            <input type="checkbox" checked="true" />
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
    todo_value: '',
    todo_list: [
      { inEdit: false, title: 'Vue.js 2.0' },
      { inEdit: false, title: 'Vuex 2.0' },
      { inEdit: false, title: 'Webpack 2.0' }
    ],
    done_list: [{ title: 'Vue-router 2.0' }]
  }),
  methods: {
    addToList: function(value) {
      this.todo_list.push({ title: value })
      this.todo_value = ''
    },
    checkFinished: function(id, isDone) {
      if (isDone) {
        this.done_list.push(this.todo_list[id])
        this.todo_list.splice(id, 1)
      }
    },
    removeTodo: function(id) {
      this.todo_list.splice(id, 1)
    },
    editTodo: function(id) {
      this.todo_list[id].inEdit = !this.todo_list[id].inEdit
    }
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
