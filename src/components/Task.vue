<template>
    <div @dblclick="$emit('toggle-reminder')" :class="[task.reminder ? 'reminder': '' , 'task']" >
        <h3>{{task.text}}
            <i @click="$emit('delete-task', task.id)" class="fa-sharp fa-solid fa-trash"></i>
        </h3>
        <P>{{task.day}}</P>
    </div>
   
</template>

<script>
    export default{
        name: 'task',
        props: {
            task: Object
        }, 
    }
</script>

<style scoped>
    .fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>