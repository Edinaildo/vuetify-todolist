<template>
  <div class="d-flex justify-center flex-column align-center">
    <v-text-field v-model="newTask.title" label="Title"></v-text-field>
    <v-text-field v-model="newTask.project" label="Project"></v-text-field>
    <v-text-field v-model="newTask.dueTo" label="Dueto"></v-text-field>
    <v-btn x-large rounded color="primary" dark @click="addTask"> Criar </v-btn>
    <!-- <v-btn x-large rounded color="primary" dark :to="{ name: 'taskList' }">
      Listar tarefas
    </v-btn> -->
  </div>
</template>

<script>
import TasksApi from '@/api/tasks.api.js'

export default {
  data: () => {
    return {
      newTask: {
        title: '',
        project: '',
        dueTo: '',
      },
    }
  },
  methods: {
    addTask() {
      TasksApi.createTask(this.newTask)
      this.$router.push({ name: 'taskList' })
    },
  },
}
</script>
