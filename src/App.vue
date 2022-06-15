<template>
  <div id = "app">
    <MyHeader />
    <MyTodoList />
    
  </div>

</template>

<script>

import MyHeader from './components/MyHeader.vue'
import MyTodoList from './components/MyTodoList.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MyTodoList
}
}
</script>

<style>
#app {
 font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
}
</style>
