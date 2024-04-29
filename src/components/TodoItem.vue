<template>
<div class="container">
    <div class="todo-item" v-bind:class= "{'is-complete':todo.completed}">
        <p>
               <input type="checkbox" v-on:change="markComplete"   v-bind:checked="todo.completed" >
               {{todo.title}}
               <button @click="update" class="update">Update</button>
              <button  @click="$emit('delete-todo',todo.id)" class="del">X</button>
        </p>

       <div>
        <div v-if="this.flag">
          <form @submit="updateTodo">
            <div class="form-group">
                  <input type="text"  v-model="updatedTitle"  placeholder="task" required class="form-control" >
            </div>
            <br>
            <div class="form-group">
                  <button class="task">update</button>
            </div>
          </form>
        </div>
       </div>

    </div>
</div>
</template>

<script>
export default {
    name:"TodoItem",
    props:['todo','todos'],
    methods: {
        markComplete(){

            this.todo.completed =! this.todo.completed
        },
        update(){

             this.flag = !this.flag

        },
        updateTodo(e){

          e.preventDefault()
          
           this.todos.filter((todo)=>{

            if(todo.id == this.todo.id){

                // update the titele

                todo.title = this.updatedTitle
            }
           })
       
        // reset the flag

        this.flag = false


        }
    },
    data(){

        return{
            flag:false,
            updatedTitle:""
        }
    }
}
</script>

<style scoped>
.todo-item{

    background: #f4f4f4;
    padding: 10px;
    margin: 20px;
    border-bottom: 1px #ccc dotted;
}

.is-complete{

    text-decoration:line-through
}

.del{

    background: rgb(164, 164, 226);
    color: #f4f4f4;
    border: none;
    padding: 5px 9px;
    border-radius: 10px;
    cursor: pointer;
    float: right;
    position: absolute;
    left: 520px;
}

.update{

    background: blue;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 20px;
    cursor: pointer;
    float: right;
    
}
.task{
    border-radius: 5px;
}

</style>