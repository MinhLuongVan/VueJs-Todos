<template>
 <AddTodo  @add-todo ="AddTodo"/>
 <MyTodoItem 
 v-for="todo in todos" 
 :key="todo.id" 
 :todoProps ="todo"
 @item-completed="markItemCompleted"
 @delete-item = "deleteItem"
 
 />
</template>

<script>
import {ref} from 'vue'
import MyTodoItem from './MyTodoItem.vue'
import AddTodo from './AddTodo.vue'
import {v4 as uuidv4} from 'uuid'
export default {
name : 'MyTodoList',
components : {MyTodoItem,AddTodo},

setup(){
    const todos = ref([
        {
            id :uuidv4(),
            title:'Việc 1',
            completed :false
        },
        {
            id :uuidv4,
            title:'Việc 2',
            completed :false
        },
        {
            id :uuidv4,
            title:'Việc 3',
            completed :false
        }
    ])
    const markItemCompleted = id =>{
        todos.value = todos.value.map(todo => {
            if(todo.id === id) todo.completed = !todo.completed;
            return todo
        })
    }
    const deleteItem = id =>{
        todos.value=todos.value.filter(todo => todo.id !==id)
    }
    const AddTodo = newTodo =>{
        todos.value.push(newTodo)
    }
    return{
        todos ,
        markItemCompleted,
        deleteItem,
        AddTodo
    }
}
}
</script>

<style>

</style>