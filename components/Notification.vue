<template>
  <div>
    <v-snackbar
      v-model="snackbar"
    >
      <div style="color: red; text-align: center; margin: 10px">
        {{ message }}
      </div>
      <slot name="close"></slot>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  name: "Notification",
  props: ['message', 'snackbar'],
}
</script>
