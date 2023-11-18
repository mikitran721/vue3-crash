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
// import {v4 as uuidv4} from 'uuid'
import axios from 'axios'

import TodoItem from './TodoItem'
import AddTodo from './AddTodo.vue';

export default {
    name:'TodosApp',
    components:{TodoItem, AddTodo },
    setup(){
        //khai bao du lieu khoi diem
        const todos=ref([])

        const getAllTodos = async()=>{
            try {
                const res = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')

                todos.value = res.data;
            } catch (error) {
                console.log(error)
            }
        }

        getAllTodos();

        //function markComplete
        const markComplete=(id)=>{
            //luc nay todos = ref
            todos.value = todos.value.map(todo =>{
                if(todo.id === id) todo.completed=!todo.completed;
                return todo;
            })
        }

        //function deleteTodo
        const deleteTodo= async (id)=>{
            try {
                //xoa o server
                await axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)

                //xoa o client
                todos.value = todos.value.filter(todo => todo.id !== id)

            } catch (error) {
                console.log(error)
            }
        }

        //addTodo function
        const addTodo = async (newTodo)=>{
            try {
                const res = await axios.post(`https://jsonplaceholder.typicode.com/todos`,newTodo)

                todos.value.push(res.data)
            } catch (error) {
                console.log(error)
            }
            // todos.value.push(newTodo)
        }

        //xuat khau data khai bao ben tren
        return {
            todos
            , markComplete
            , deleteTodo
            ,addTodo
            // , getAllTodos
        }
    }
}
</script>

<style>
.container{
    display: block;
}
</style>