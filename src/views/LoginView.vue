<template>
  <div>
    <v-layout align-center justify-center class="centralizar">
      <v-flex xs12 sm8 md4>
        <v-card class="elevation-12">
          <v-toolbar dark color="primary">
            <v-toolbar-title>Entrar</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <v-form>
              <v-text-field
                v-model="username"
                name="usuario"
                label="Usuario"
                type="text"
                required
                outlined
              ></v-text-field>
              <v-text-field
                v-model="password"
                id="senha"
                name="senha"
                label="Senha"
                type="password"
                required
                outlined
              ></v-text-field>
              <p><a>Esqueci a minha senha</a></p>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-spacer
              ><v-btn large rounded color="primary" @click="login"
                >Entrar</v-btn
              ></v-spacer
            >
            <v-btn large rounded color="error" :to="{ name: 'cadastrar' }"
              >Cadastrar</v-btn
            >
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import AuthApi from '@/api/auth.api.js'

export default {
  data: () => {
    return {
      loading: false,
      valid: false,
      username: '',
      password: '',
      snackbar: {
        show: false,
        message: '',
      },
    }
  },
  methods: {
    login() {
      this.loading = true
      AuthApi.login(this.username, this.password)
        .then((user) => {
          console.log('login ok', user)
          this.saveLoggedUser(user)
          this.$router.push({ name: 'painel' })
        })
        .catch((error) => {
          console.log('login falhou', error)
          this.snackbar.message = 'Usuario ou senha invalida'
          this.snackbar.show = true
        })
        .finally(() => {
          this.loading = false
        })
    },
    saveLoggedUser(user) {
      window.localStorage.setItem('loggedUser', user.id)
      window.localStorage.setItem('loggedUserToken', user.token)
    },
  },
}
</script>

<style scoped>
.centralizar {
  margin: 100px;
}
</style>
