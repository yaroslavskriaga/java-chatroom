<template>
  <v-app>
    <v-navigation-drawer :value="sidebar" app mobile-break-point="600">
      <new-room></new-room>
      <v-divider></v-divider>
      <room-list></room-list>
    </v-navigation-drawer>

    <v-app-bar app color="blue" dark>
      <v-row justify="end">
        <v-toolbar-items>
          <v-btn color="error"   to="/" x-large v-if="username">Exit</v-btn>
          <v-btn color="error"   to="/" x-large v-else>Join</v-btn>
          <v-btn color="sucess" outlined  to="/chat" x-large>Chat</v-btn>
        </v-toolbar-items>
      </v-row>
    </v-app-bar>

    <v-content>
      <v-container fluid fill-height>
        <v-layout align-top justify-center mt-12>
          <nuxt />
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import NewRoom from "@/components/room/NewRoom.vue";
import RoomList from "@/components/room/RoomList.vue";
export default {
  components: {
    NewRoom,
    RoomList
  },
  computed: {
    sidebar() {
      return this.$store.getters["main/sidebar"];
    },
    username() {
      return this.$store.getters["main/username"];
    }
  }
};
</script>

<style>
</style>