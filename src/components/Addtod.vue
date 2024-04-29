<template>

<div class="head">

    <h1 class="first">Todos App</h1>
    <br>
    <div class="container">
    
    <!-- an event submit is created and addtodo method is created this method automatically executes hen the form submits -->

    <form @submit="addTodo" > 
    <div class="form-group">
    <input   type="text" name="title"   v-model="title"  class="form-control" placeholder="Task" >
    
    </div>
    <br>
    
    <div class="">
    
    <button style="position: relative; left:200px ;" class="btn btn-danger  ">Add todo</button>
    
    </div>


    </form>
    </div>
    
</div>




</template>

<script>
export default {

    name:'Addtod',
    data(){
    
    return{
    
    title:""
    
    }
    
    },

    methods:{
        addTodo(e){
            e.preventDefault()

            const newTodo ={

                id: Date.now(),
                title:this.title,
                completed:false
            }

            // send out a events

            this.$emit("add-todo",newTodo)

            // clear out input field

            this.title = ""
        }
    }

}
</script>

<style scoped>

.form-group input{

width: 500px;

}

.first{

    color: blue;
}

</style>