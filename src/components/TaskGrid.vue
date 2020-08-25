<template>
  <div class="task-grid">
      <template v-if="tasks.length">
        <Task v-for="(task, i) in tasks" :key="task.name" 
              :task="task" 
              @taskDeleted="deletedTask(i)"
              @taskStateChanged="stateChanged(i)">
              </Task>
      </template>
      
      <p class="no-task" v-else>
        Sem Tarefas cadastradas...
      </p>
  </div>
</template>

<script>
import Task from '@/components/Task';
export default {
  props: {
    tasks: { type: Array, required: true }
  },
  components: { Task },
  methods: {
    stateChanged(i) {
      this.$emit('taskStateChanged', i);
    },
    deletedTask(i) {
      this.$emit('taskDeleted', i);
    }
  }
}
</script>

<style>
  .task-grid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }

  .task-grid .task {
    margin: 10px;
  }

  .no-task {
    color: #AAA;
    font-size: 1.7rem;
  }

</style>