<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="password"
            :rules="passwordRules"
            :counter="10"
            label="Password"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>
      </v-row>
    </v-container>

    <div class="form-group row mb-0">
      <div class="col-md-8 offset-md-4">
        <button type="submit" class="btn btn-primary">
          Login
        </button>
      </div>
    </div>
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
      await this.$router.push({
        path: '/'
      });
    }
  }
}
</script>
