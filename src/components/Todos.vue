<template>
  <TodoItem v-for="todo in todos" 
  :key="todo.id" 
  :todoProps="todo"
  @item-completed="markComplete"
  @delete-item="deleteTodo"
  />
</template>

<script>
import { ref } from 'vue'; //su dung khoi diem
import TodoItem from './TodoItem'

export default {
    name:'TodosApp',
    components:{TodoItem},
    setup(){
        //khai bao du lieu khoi diem
        const todos=ref([
            {
                id:1,
                title:'Viec 1',
                completed:false
            },
            {
                id:2,
                title:'Viec 2',
                completed:false
            },
            {
                id:3,
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

        //xuat khau data khai bao ben tren
        return {
            todos
            , markComplete
            , deleteTodo
        }
    }
}
</script>

<style>

</style>