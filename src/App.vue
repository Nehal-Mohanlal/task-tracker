<template>
  <div class="container">
    <HeaderOne title = 'Task Tracker'/> 
    <addTask @add-task="addTask" />
    <Tasks @toggle-reminder="toggleRemider" @delete-task="deleteTask" :tasks="tasks" />
  </div>
 
</template>

<script>
import HeaderOne from './components/HeaderOne.vue'
import Tasks from './components/Tasks.vue'
import addTask from './components/addTask.vue' 

export default {
  name: 'App',
  components: {
    HeaderOne, 
    Tasks, 
    addTask
  },
  data(){
    return{
      tasks: []
    }
  }, 
  methods:{
      addTask(task){
        this.tasks = {...this.tasks, task}
      },
      deleteTask(id){
        if(confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task)=> task.id !== id)
      }  
    },
      toggleRemider(id){
        this.tasks = this.tasks.map((task)=> task.id === id 
        ? {...task, reminder: !task.reminder}: task
        )
      }
  }, 
  created(){
    this.tasks = [
      {
        id:1, 
        text: 'Meeting at School', 
        day: 'March 3rd at 1:30pm', 
        reminder: true
      },
      {
        id:2, 
        text: 'Dentist', 
        day: 'March 6th at 3:30pm', 
        reminder: true
      },
      {
        id:3, 
        text: 'Pick up dry cleaning', 
        day: 'April 3rd at 8:30am', 
        reminder: true
      },
      {
        id:4, 
        text: 'Appointment', 
        day: 'May 4th at 1:30pm', 
        reminder: true
      }
    ]
  }

  }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
