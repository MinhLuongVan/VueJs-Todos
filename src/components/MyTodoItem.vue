<template>
  <p :class="['todo-item',todoProps.completed ? 'is-completed' :'']">
    <input type="checkbox" :checked="todoProps.completed"
     @change="markItemCompleted"/>
    {{todoProps.title}}
    <button class="btn-del" @click="deleteItem">Delete</button>
  </p>
</template>

<script>
export default {
name : 'MyTodoItem',
props :['todoProps'],
setup(props,context){
    const markItemCompleted = () =>{
       context.emit('item-completed',props.todoProps.id)
    }
    const deleteItem =() =>{
        context.emit('delete-item',props.todoProps.id)
    }

    return{
        markItemCompleted:markItemCompleted,
        deleteItem
    }
}
}
</script>

<style>
.todo-item{
    background: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: 1px #ccc dotted;
}
.is-completed{
    text-decoration: line-through;
}
.btn-del {
    background: red;
    color: #fff;
    border: none;
    cursor: pointer;
    float:right;
}
</style>