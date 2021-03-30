<template>
  <v-card
    class="mx-auto overflow-hidden"
    height="auto"
    width="auto"
  >
    <v-system-bar color="deep-purple darken-3"></v-system-bar>

    <v-app-bar
      color="deep-purple accent-4"
      dark
      prominent
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title style="text-align: center">Caspian Transplantation</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      fixed
      top
      temporary
      width="25%"
      style="background: aliceblue"
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >

          <template v-if="!loggedIn">
            <v-list-item>
              <v-list-item-title style="text-align: center" href="">
                <nuxt-link :to="{ name: 'register' }" style="text-align: center">
                  ثبت نام
                </nuxt-link>
              </v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title style="text-align: center" href="">
                <nuxt-link :to="{ name: 'login' }" style="text-align: center">
                  ورود
                </nuxt-link>
              </v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title style="text-align: center" href="">کاسپین</v-list-item-title>
            </v-list-item>
          </template>

          <template v-if="loggedIn">
            <v-list-item>
              <v-list-item-title style="text-align: center" href="">{{user.firstname + user.lastname}}</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title style="text-align: center" href="">کاسپین</v-list-item-title>
            </v-list-item>

            <v-list-item>
              <v-list-item-title style="text-align: center" @click.prevent="logout">خروج</v-list-item-title>
            </v-list-item>
          </template>

        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-card-text style="text-align: center">
      Caspian
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "navbar",
  data: () => ({
    drawer: false,
    group: null,
  }),
  watch: {
    group() {
      this.drawer = false
    },
  },
  methods: {
    logout() {
      this.$auth.logout();
    }
  }
}
</script>

<style scoped>

</style>
