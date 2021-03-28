<template>
  <div v-if="loggedIn">
    name : {{user.lastname}}
  </div>
  <div v-else>
    caspian
  </div>
</template>

<script>

export default {
}
</script>
