<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/todo.png')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">CRUD Vuetify</h1>

        <p class="subheading font-weight-regular">
          Lista de tarefas usando VueJS + Vuetify + API Mock
        </p>
        <p>
          <v-btn large rounded class="teal lighten-2" :to="{ name: 'login' }">
            Iniciar
          </v-btn>
        </p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {}
</script>
