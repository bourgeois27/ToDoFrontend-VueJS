<template>
  <div>
    <form class="form-inline mt-2">
      <label for="task" class="sr-only">Task</label>
      <input autocomplete="off" type="text" class="form-control" id="task" placeholder="Enter task" v-model="newTask" @keydown.enter.prevent="addTask">
      <a id="add-btn" class="btn btn-dark mb-2" @click.prevent="addTask">Add</a>
      <a class="btn btn-danger mb-2" @click.prevent="clearInput">Cancel</a>
    </form>
    <small class="form-text text-muted">
      Fill in the following form and click the add button to submit your new task and add it to your todo list.
    </small>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: ''
    }
  },
  methods: {
    clearInput() {
      this.newTask = '';
    },
    addTask() {
      if(this.newTask.length > 0) {
        this.$emit("addNewTask", this.newTask);
        this.clearInput();
      }
    }
  }
}
</script>

<style scoped>
#add-btn {
  margin-left: 10px;
  margin-right: 10px; 
}

a.btn, a.btn:hover {
  color: white;
}
</style>
