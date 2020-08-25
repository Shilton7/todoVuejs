<template>
  <div id="app">
   <h1>Tarefas Shilton</h1>

   <NewTask @taskAdded="addTask"></NewTask>

   <TaskGrid 
          :tasks="tasks"
          @taskDeleted="deleteTask"
          @taskStateChanged="toggleTaskState"></TaskGrid>
   
  </div>
</template>

<script>
import TaskGrid from '@/components/TaskGrid';
import NewTask from '@/components/NewTask';
export default {
  name: 'App',
  components: {TaskGrid, NewTask},
  data() {
    return {
      tasks: [
        { name: 'Estudar', pending: false },
        { name: 'Comprar Sapato', pending: true },
      ]
    }
  },
  methods: {
    addTask(task) {
      const existsName = t => t.name === task.name;
      const reallyNew = this.tasks.filter(existsName).length == 0;
      if(reallyNew){
        this.tasks.push({
          name: task.name,
          pending: true
        })
      }
    },
    deleteTask(i){
      this.tasks.splice(i,1);
    },
    toggleTaskState(i) {
      this.tasks[i].pending = !this.tasks[i].pending;
    }
  }
}
</script>

<style>
  body {
    font-family: 'Lato', sans-serif;
    background: rgb(2,0,36);
    background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(9,9,121,1) 12%, rgba(0,212,255,1) 92%);
    color: #FFF;
}
#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
