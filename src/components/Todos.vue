<template>
  <TodoItem v-for="todo in todos" v-bind:key="todo.id" v-bind:todoProps="todo" />
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
                id:1,
                title:'Viec 2',
                completed:false
            },
            {
                id:1,
                title:'Viec 3',
                completed:true
            },
        ])

        //xuat khau data khai bao ben tren
        return {
            todos
        }
    }
}
</script>

<style>

</style>