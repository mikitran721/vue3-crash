<template>
    <div  class="container">

        <AddTodo @add-todo="addTodo" />
        <TodoItem v-for="todo in todos" 
        :key="todo.id" 
        :todoProps="todo"
        @item-completed="markComplete"
        @delete-item="deleteTodo"
        />
    </div>
</template>

<script>
import { ref } from 'vue'; //su dung khoi diem
import {v4 as uuidv4} from 'uuid'
import TodoItem from './TodoItem'
import AddTodo from './AddTodo.vue';

export default {
    name:'TodosApp',
    components:{TodoItem, AddTodo },
    setup(){
        //khai bao du lieu khoi diem
        const todos=ref([
            {
                id:uuidv4(),
                title:'Viec 1',
                completed:false
            },
            {
                id:uuidv4(),
                title:'Viec 2',
                completed:false
            },
            {
                id:uuidv4(),
                title:'Viec 3',
                completed:true
            },
        ])

        //function markComplete
        const markComplete=(id)=>{
            //luc nay todos = ref
            todos.value = todos.value.map(todo =>{
                if(todo.id === id) todo.completed=!todo.completed;
                return todo;
            })
        }

        //function deleteTodo
        const deleteTodo=id=>{
            todos.value = todos.value.filter(todo => todo.id !== id)
        }

        //addTodo function
        const addTodo = (newTodo)=>{
            todos.value.push(newTodo)
        }

        //xuat khau data khai bao ben tren
        return {
            todos
            , markComplete
            , deleteTodo
            ,addTodo
        }
    }
}
</script>

<style>
.container{
    display: block;
}
</style>