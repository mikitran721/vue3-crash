<template>
  <p v-for="todo in todos" v-bind:key="todo">{{ todo }}</p>
</template>

<script>
import { ref } from 'vue'; //su dung khoi diem

export default {
    name:'TodosApp',
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