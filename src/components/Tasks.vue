<template>
  <div>
    <h1 class="display-5">Your tasks :</h1>
    <ul class="list-group">
      <li
        v-if="!tasks.length"  
        class="list-group-item">
        You don't have any tasks on your todo list so far
      </li>
      <li
        v-else
        class="list-group-item"
        v-for="(task, index) in tasks"
        :key="task.id">
        <app-task
          :task="task"
          :index="index"
          @editTask="editTask"
          @deleteTask="deleteTask">
        </app-task>
      </li>
    </ul>
    <hr>
    <h1 class="display-5">Add a task :</h1>
    <app-form
      @addNewTask="addNewTask">
    </app-form>
  </div>
</template>

<script>
import * as api from '../api';

import Task from './Task';
import Form from './Form';

export default {
  components: {
    appTask: Task,
    appForm: Form
  },
  data() {
    return {
      userId: '',
      tasks: []
    }
  },
  async created() {
    this.userId = await api.getUser();
    this.tasks = await api.getTasks(this.userId);
  },
  methods: {
    async addNewTask(taskName) {
      await api.createTask(this.userId, taskName)
        .then((task) => {
          this.tasks.push(task);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    async editTask(task) {
      const editedTask = await api.editTask(this.userId, task.id, task.newName)
        .then(() => {
          this.tasks[task.index].name = task.newName;
        });
    },
    async deleteTask(task) {
      await api.deleteTask(this.userId, task.id)
        .then(() => {
          this.tasks.splice(task.index, 1);
        });
    }
  }
}
</script>

<style scoped>

</style>

