<template>
  <div>
    <h1>Learn Vuex 2.0 Todo List</h1>
    <input type="text" placeholder="add Todo.." />
    <button type="button">新增</button>
    <div class="center-inline">
      <div>
        <h3>Todo List</h3>
      </div>
      <div>
        <h3>Done List</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({})
}
</script>

<style>
.center-inline {
  margin: 0px auto;
  text-align: center;
}

.center-inline div {
  display: inline-block;
  width: 150px;
}
</style>
