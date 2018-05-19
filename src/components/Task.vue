<template>
  <div class="row justify-content-between">
    <div class="col-4">
      <div v-if="!editable">
        <p>{{ task.name }}</p>
      </div>
      <div v-else>
        <input
          type="text"
          v-model="renamedTask"
          v-bind:placeholder="task.name"
          @keydown.enter="editTask"/>
        <button class="btn btn-dark" @click="editTask">
          Apply
        </button>
      </div>
    </div>
    <div class="col-8">
      <div class="row justify-content-end mr-1">
        <div class="col-1">
          <i
            class="fas fa-edit"
            @click="editable = !editable">
          </i>
        </div>
        <div class="col-1">
          <i
            class="fas fa-trash"
            @click="deleteTask">
          </i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      renamedTask: '',
      editable: false
    }
  },
  methods: {
    editTask() {
      this.$emit("editTask", { id: this.task.id, newName: this.renamedTask, index: this.index });
      this.editable = false;
    },
    deleteTask() {
      this.$emit("deleteTask", { id: this.task.id, index: this.index });
    }
  }
}
</script>

<style scoped>
input[type="text"] {
  border: 1px solid #ced4da;
  line-height: 2;
  color: #495057;
  border-radius: .25rem;
  font-size: 1rem;
}

i.fa-edit:hover {
  color: blue;
}

i.fa-trash:hover {
  color: red;
}
</style>
