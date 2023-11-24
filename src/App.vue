<template>
  <div>
    <h1>Hello from Aniruddha</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue"
export default {
    namw: "App",
    components: {
        TodoList
    }
}
</script>

<style>
    body{
        background-color: rgb(66, 66, 66);
        color: aliceblue;
    }
</style>