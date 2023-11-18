<template>
  <!-- <p class="todo-item is-completed" :id="new_id">  -->
  <p :class="['todo-item', todoProps.completed ? 'is-completed' :'']">
    <input @change="markItemCompleted" type="checkbox" :checked="todoProps.completed"/>
    {{ todoProps.title }}
    <button class="del-btn" @click="deleteItem">Delete</button>
  </p>
</template>

<script>
// import { ref } from 'vue';
export default {
    name:'TodoItem',
    props:['todoProps'] //cac props o day
    // ,setup(){
    //   const new_id=ref('my-new-id')
    //   return{
    //     new_id
    //   }
    // }
    ,setup(props,context){
      const markItemCompleted =()=>{
        //goi function tu parent component
        context.emit('item-completed',props.todoProps.id)
        // console.log(props.todoProps)
      }

      const deleteItem=()=>{
        //goi function tu parents
        context.emit('delete-item',props.todoProps.id)
      }

      return {
        markItemCompleted
        , deleteItem
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
  .del-btn{
    background: #ff0000;
    color: #fff;
    border: none;
    cursor: pointer;
    float: right;
  }
</style>