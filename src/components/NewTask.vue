<template>
  <div class="new-task">
    <input type="text" class="form-element" placeholder="Nova Tarefa ?"
           v-model="name" @keydown.enter="addTask"/>

    <button class="form-element" @click="addTask">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: ''
    }
  },
  methods: {
    addTask() {
      if(this.name.length){
        this.$emit('taskAdded', { name: this.name})
        this.resetInput();
      }
    },
    resetInput() {
      this.name = '';
    }
  }

}
</script>

<style>
  .new-task {
    margin: 35px;;
  }

  .form-element {
    outline: none;
    font-size: 2rem;
    border: 1px solid #FFF;
    padding: 5px 10px 8px;
    color: #FFF;
  }

  input.form-element {
    width: 500px;
    background: #FFF2;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
  }

  button.form-element {
    border-left: none;
    background-color: #0a8F08;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;

  }

</style>