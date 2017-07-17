<template>
  <div >
    <input class="toDoEntry"
    v-model="newTodoText"
    v-on:keyup.enter="addNewTodo"
    placeholder="Add to list"
    >
    <li
     v-for="(todo, index) in this.data"
     v-bind:key="index"
     v-bind:title="todo.name"
     v-show="!todo.completed">
     <input type="button" id="checkbox"v-on:click="completed(index,todo.completed )"  >
     {{todo.name}}
     <button v-on:click="remove(index)">X</button>

    </li>
    <span>{{newTodoText}}</span>
  </div>
</template>

<script>
export default {
  name: 'tolistInputBlock',
  props:['data'],
  data () {
    return {
      newTodoText:'',
      checked:'',

    }
  },
  methods:{
    addNewTodo : function (){
      console.log(this.data);
      this.data.push({name:this.newTodoText,completed: false});
      this.newTodoText = '';
    },
    remove : function(index){
      this.data.splice(index, 1)
    },
    completed:function(index, value){
      this.data[index].completed = !value
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
.toDoEntry{
  width: 35%;
height: 44px;
}
.hello{
  background-color: palevioletred;
}

</style>
