<template>
  <div id="app">
   <h1>Tarefas Shilton</h1>
   <TaskGrid :tasks="tasks"></TaskGrid>
  </div>
</template>

<script>
import TaskGrid from '@/components/TaskGrid';
export default {
  name: 'App',
  components: {TaskGrid},
  data() {
    return {
      tasks: [
        { name: 'Estudar', pending: false },
        { name: 'Comprar Sapato', pending: true },
      ]
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
