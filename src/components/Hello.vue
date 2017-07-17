<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-show="toNav">
      <h2>Pending Tasks</h2>
        <ul>
          <TolistInputBlock :data = "todolist"></TolistInputBlock>
         </ul>
    </div>
    <div v-show="!toNav">
      <h2>completed Tasks</h2>
        <CompletedTasks :data = "todolist"></CompletedTasks>
    </div>
    <div >
      <button @click ="changeTask(true)">Current Tasks</button>
      <button  @click ="changeTask(false)">Completed Taskes</button>
    </div>

  </div>
</template>

<script>
import TolistInputBlock from './tolistInputBlock.vue'
import CompletedTasks from './CompletedTasks'
export default {
  name: 'hello',
  components:
    {
      TolistInputBlock,
      CompletedTasks
    },
  data () {
    return {
      msg: 'Welcome to My App',
      message: 'Essential Links here',
       toNav:true,
      todolist:[
        {name:'sanal',completed: false},
        {name:'akhil',completed: false},
        {name:'yathi',completed: false}
      ]
    }
  },
  methods:{
    changeTask:function(value){
      this.toNav = value;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
  width: 270px;
    height: 70px;
    background-color: #c08ece;
    text-align: center;
    border: none;
    color: azure;
    font-weight: 900;
    font-size: x-large;
}
input{
  width: 35%;
  height: 44px;
}
.hello{
  background-color: palevioletred;
  margin-left: 20%;
  margin-right: 20%;
}


</style>
