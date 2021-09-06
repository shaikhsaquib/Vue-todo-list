<template>
    <div class="column is-multiline ">
        <div class="column is-6 is-offset-3">
            <div class="box">
                <form @submit.passive="onSubmit">
                    <div class="field">
                        <label class="label"> Add yor todo</label>
                        <div class="control">
                        <input class="input" type="text" placeholder="enter your todo.." v-model="title"/>
                        </div>
                    </div>
                </form>
            </div>
        </div>
        <div class="column is-6 is-offset-3" v-for="todo in todos" :key="todo.id">
            <div class="box todo_box" @click="$emit('oncomplete',todo.id)">
                <span :class="{completed:todo.completed}">{{todo.title}}</span>
                <button class="button is-danger is-small is-pulled-right"  @click="$emit('ondelete',todo.id)"  v-if="todo.completed"> delete</button>
                </div>
        </div>
    </div>
</template>
<script>
import shortid from 'shortid'
export default {
   name:'todos', 
   props:["todos"],
   data(){
       return{
           title:"",
           }
   },
   methods:{
       onSubmit(){
           const new_todo={
               this:this.title,
               completed:false,
               id:shortid.generate(),
           };
           this.$emit("addTodo",new_todo);
           this.title=""
       }
   }
}
</script>
<style scoped>
.completed{
    text-decoration: line-through;
}
.todo_box{
    transition: all 0.3s;

}
.todo_box:hover{
    cursor: pointer;
    background-color: wheat;
    transform: scale(1.1);
    
}
</style>