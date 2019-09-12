<template>
  <v-flex xs12 sm5 v-if="username" text-center>
    <p>
      Welcome,
      <b>{{ username }}</b>! Please, create the room or join one for chatting.
    </p>
  </v-flex>

  <v-flex xs12 sm5 v-else text-center>
    <p>Welcome, guest! Please, register for chatting</p>
  </v-flex>
</template>

<script>
export default {
  fetch({ store }) {
    store.commit("main/showSidebar", true);
    store.dispatch("websocket/connect");
  },
  layout: "chat",
  computed: {
    username() {
      return this.$store.getters["main/username"];
    }
  }
};
</script>

<style scoped>
</style>