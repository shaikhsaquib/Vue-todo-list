<template>
  <div class="section">
    <div class="container">
      <todos :todos="todos" @onaddTodo="addTodo" @oncomplete="complete" @ondelete="delet"/>
    </div>
  </div>
</template>

<script>
import  "bulma/css/bulma.css";
import todos from './components/todos.vue'
export default {
  name: 'App',
  components: {
  todos
  },
  data(){
    return{
      todos:[
        {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false
  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": false
  },
  {
    "userId": 1,
    "id": 4,
    "title": "et porro tempora",
    "completed": true
  },
  {
    "userId": 1,
    "id": 5,
    "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
    "completed": false
  },
  {
    "userId": 1,
    "id": 6,
    "title": "qui ullam ratione quibusdam voluptatem quia omnis",
    "completed": false
  },
    ]}
  },
  methods:{
    addTodo(todo){
      this.todos.unshift(todo)
    },
    complete(id){
      const updatedTodos=this.todos.map(todo=> todo.id == id ? Object.assign(todo,{completed: true}): todo);
      this.todo=updatedTodos 
    },
    delet(id){
      let deleted_todos=this.todos.filter(todo=>todo.id !=id)
      this.todos=deleted_todos
    }
  }
}
</script>

<style>
#app {
  background-color:cornflowerblue;
  font-family: "serif";
  text-align: center;
  min-height: 100vh;

}
</style>
