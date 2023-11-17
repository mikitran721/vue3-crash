<template lang="">
    <div id="app">
        <HeaderApp />
        <TodosApp />
    </div>
</template>
<script>
import HeaderApp from './components/Header.vue';
import TodosApp from './components/Todos.vue'
export default {
    name:'App',
    components:{ HeaderApp, TodosApp }
}
</script>
<style lang="css">
    #app{
        font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }
</style>