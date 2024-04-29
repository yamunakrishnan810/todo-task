<script>

import Todos from "./components/Todos.vue";
import Addtod from "./components/Addtod.vue";

export default {
  components: { Todos, Addtod } ,
  data(){

    return{
      todos:[

       {
        id:'1',
        title:'todo  1',
        completed:false
       },
       {
        id:'2',
        title:'todo  2',
        completed:true
       },
       {
        id:'3',
        title:'todo  3',
        completed:false
       },
       {
        id:'4',
        title:'todo  4',
        completed:true
       }




      ]
    }
  },
  
  
  methods:{
    addTodo(todo){

      // adding the todo to the todos array

      this.todos = [...this.todos,todo]

    },

    deleteTodo(id){

      this.todos = this.todos.filter((todo)=>todo.id !== id)
    }
  }// Register both components
}


</script>

<template>
  <div>
  
<Addtod v-on:add-todo="addTodo" />    
<Todos v-on:delete-todo="deleteTodo"  v-bind:todos="todos"/>
<!-- importing the 2ccomponents from components folder -->
  
  </div>
</template>

<style scoped>

</style>
