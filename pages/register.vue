<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="userForm.firstname"
            :rules="nameRules"
            :counter="10"
            label="First name"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="userForm.lastname"
            :rules="nameRules"
            :counter="10"
            label="Last name"
            required
          ></v-text-field>
        </v-col>

        <v-col
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
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="userForm.phoneNumber"
            :rules="phoneNumberRules"
            label="Phone Number"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-textarea
            v-model="userForm.address"
            :rules="addressRules"
            label="Address"
            required
          ></v-textarea>
        </v-col>

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="userForm.password"
            :rules="passwordRules"
            label="password"
            type="password"
            required
          ></v-text-field>
        </v-col>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="userForm.password_confirmation"
            :rules="passwordConfirmationRules"
            label="passwordConfirmation"
            type="password"
            required
          ></v-text-field>
        </v-col>
      </v-row>
      <v-row style="text-align: center">
        <v-col style="margin: 0 auto"
               cols="12"
               md="4"
        >
          <v-btn elevation="2" block @click="register">
            register
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
  name: "register",

  data: () => ({
    valid: false,
    firstname: '',
    lastname: '',
    nameRules: [
      v => !!v || 'Name is required',
      v => v.length <= 10 || 'Name must be less than 10 characters',
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid',
    ],
    phoneNumber: '',
    phoneNumberRules: [
      v => !!v || 'phoneNumberRules is required',
      v => v.length <= 11 || 'phoneNumberRules must be valid',
    ],
    address: '',
    addressRules: [
      v => !!v || 'addressRules is required',
      v => v.length > 5 || 'addressRules must be valid',
    ],
    password: '',
    passwordRules: [
      v => !!v || 'passwordRules is required',
      v => v.length >= 8 || 'passwordRules must be valid',
    ],
    passwordConfirmation: '',
    passwordConfirmationRules: [
      v => !!v || 'passwordRules is required',
      v => v.length >= 8 || 'passwordRules must be valid',
    ],

    userForm: {
      firstname: '',
      lastname: '',
      email: '',
      password: '',
      password_confirmation: '',
      phoneNumber: '',
      address: '',
    }
  }),

  methods: {
    async register() {
      await this.$axios.post('register', this.userForm);
      this.$auth.login({
        data: this.userForm
      })
    }
  }
}
</script>

<style scoped>

</style>
