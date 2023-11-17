<template>
  <TodoItem v-for="todo in todos" v-bind:key="todo" v-bind:todoProps="todo" />
</template>

<script>
import { ref } from 'vue'; //su dung khoi diem
import TodoItem from './TodoItem'

export default {
    name:'TodosApp',
    components:{TodoItem},
    setup(){
        //khai bao du lieu khoi diem
        const todos=ref(['Viec 1','Viec 2','Viec 3'])

        //xuat khau data khai bao ben tren
        return {
            todos
        }
    }
}
</script>

<style>

</style>