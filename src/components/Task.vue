<template>
  <div class="task" :class="stateClass">
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
  }
}
</script>

<style>
  .task {
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
</style>