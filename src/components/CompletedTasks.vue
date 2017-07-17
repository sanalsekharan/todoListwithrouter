<template >

  <ul>
    <li
     v-for="(todo, index) in this.data"
     v-bind:key="index"
     v-bind:title="todo.name"
     v-show="todo.completed">
     <input type="button"  id="checkbox"v-on:click="completed(index,todo.completed)" >
     {{todo.name}}
     <button v-on:click="remove(index)">X</button>

    </li>
   </ul>

</template>

<script>
export default {
  name: 'CompletedTasks',
  props:['data'],
  data () {
    return {
      newTodoText:'',
      checked:'',

    }
  },
  methods:{
    addNewTodo : function (){
      console.log(this.props.data);
      this.data.push({name:this.newTodoText,completed: false});
      this.newTodoText = '';
    },
    remove : function(index){
      this.data.splice(index, 1)
    },
    completed:function(index,value){
      this.data[index].completed = !value
    },
    changeTask:function(value){
      this.toNav = value;
    }
  }


}
</script>

<style scoped>
h1, h2 {
  background-color: cornflowerblue;
  font-weight: normal;

}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: block;
  margin: 0 10px;
}
button{
    background-color: rgba(44, 145, 202, 0.53);;
    text-align: center;
    border: none;
    color: azure;
    font-weight: 900;
    font-size: x-large;
}

.hello{
  background-color: palevioletred;
  margin-left: 20%;
  margin-right: 20%;
}

</style>
