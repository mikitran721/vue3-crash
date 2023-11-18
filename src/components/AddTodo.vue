<template>
  <form @submit="addItem">
    <input type="text" placeholder="new todo..." v-model="title">
    <input type="submit" value="Them" class="add-btn">
  </form>
</template>

<script>
import { ref } from 'vue';
// import {v4 as uuidv4} from 'uuid'

export default {
    name:'AddTodo'
    ,setup(props,context){
        const title=ref(''); //gia tri ban dau
        /* const check=()=>{
            console.log(title.value)
        } */

        //addItem function
        const addItem=(event)=>{
            event.preventDefault();

            const newItem={
                // id:uuidv4(),
                title:title.value,
                completed:false
            }

            context.emit('add-todo',newItem)

            //reset value of input
            title.value = '';
        }
        return {
            title
            // ,check
            ,addItem
        }
    }
}
</script>

<style scoped>
    form{
        display: flex;
        background-color: rgb(255, 255, 255)040;
    }
    input[type='text']{
        flex:10;
        padding: 5px;
    }

    input[type='submit']{
        flex:2;
        /* so cot */
    }
</style>