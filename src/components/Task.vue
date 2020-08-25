<template>
  <div class="task" :class="stateClass" @click="setStatePending(task)">
    <span class="close" @click.stop="removeTask(task)">x</span>
    <p>{{task.name}}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: { type: Object, required: true }
  },
  computed: {
      stateClass() {
        return {
          pending: this.task.pending,
          done: !this.task.pending
        }
      }
  },
  methods: {
    removeTask(task) {
      this.$emit('taskDeleted', { task })
    },
    setStatePending(task){
      this.$emit('taskStateChanged', task);
    }
  }
}
</script>

<style>
  .task {
    position: relative;
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2rem;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .pending {
    background: #F44336;
    border-left: 12px solid #B73229;
  }
  .done {
    color: #DDD;
    text-decoration: line-through;
    background: #4CAF50;
    border-left: 12px solid #0a8F08;
  }

  .pending .close {
    background-color: #B73229;
  }

  .done .close {
    background-color: #0A8F08;
  }

  .close {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
  }

</style>