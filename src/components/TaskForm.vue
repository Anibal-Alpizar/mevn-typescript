<template>
  <div class="col-md-4 offset-md-4 mt-4">
    <form @submit.prevent="saveTask()" class="card card-body">
      <h1 class="text-center h3 mb-3">Create Task</h1>
      <input
        type="text"
        placeholder="Write a title"
        v-model="task.title"
        class="form-control mb-3"
        autofocus
      />
      <textarea
        rows="3"
        placeholder="Write a description"
        v-model="task.description"
        class="form-control mb-3"
      ></textarea>
      <button
        type="submit"
        class="btn btn-primary"
        :disabled="!task.title || !task.description"
      >
        Create Task
      </button>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { Task } from "../interfaces/Task";
import { createTask } from "../services/TaskService";

export default defineComponent({
  data() {
    return {
      task: {} as Task,
    };
  },
  methods: {
    async saveTask() {
      const res = await createTask(this.task);
      console.log(res);
      this.$router.push("/");
    },
  },
});
</script>
