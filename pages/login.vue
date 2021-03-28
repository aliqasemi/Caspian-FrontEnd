<template>
  <v-form v-model="valid">
    <v-container style="background: antiquewhite; margin-top: 20px; width: 50%">
      <v-row style="margin: 0 auto">
        <v-col style="margin: 0 auto"
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="userForm.email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>
      </v-row>

      <v-row style="margin: 0 auto">
        <v-col style="margin: 0 auto"
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="userForm.password"
            :rules="passwordRules"
            :counter="10"
            label="Password"
            required
          ></v-text-field>
        </v-col>
      </v-row>


      <v-row style="text-align: center">
        <v-col style="margin: 0 auto"
          cols="12"
          md="4"
        >
          <v-btn elevation="2" block @click="addUser">
            Login
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>
<script>
export default {
  name: 'login',
  data: () => ({
    valid: false,
    password: '',
    passwordRules: [
      v => !!v || 'Password is required',
      v => v.length <= 10 || 'Name must be less than 10 characters',
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid',
    ],

    userForm: {
      email: '',
      password: ''
    }
  }),

  methods: {
    async addUser() {
      await this.$auth.login({
        data: this.userForm
      });
    }
  }
}
</script>
