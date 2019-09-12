<template>
  <v-list>
    <v-subheader>Create a new chatroom</v-subheader>
    <v-list-item-content>
      <form @submit.prevent="addRoom">
        <v-text-field
          label="Chatroom name..."
          name="roomname"
          type="text"
          :rules="[rules.required]"
          ref="roomname"
          v-model="roomname"
        ></v-text-field>
      </form>
      <v-btn v-if="!username" color="blue" @click="addRoom" disabled>
        <v-icon color="white">add</v-icon>
      </v-btn>
      <v-btn v-else color="blue" @click="addRoom" >
        <v-icon color="white">add</v-icon>
      </v-btn>
    </v-list-item-content>
  </v-list>
</template>

<script>
export default {
  data() {
    return {
      roomname: "",
      rules: {
        required: value => !!value || "Room name is required"
      }
    };
  },
  methods: {
    addRoom() {
      const isValid = this.$refs["roomname"].validate(true);
      if (isValid) {
        this.$store.dispatch("main/addRoom", this.roomname);
        this.$refs["roomname"].reset();
      }
    },
    roomKey(roomName) {
      return roomName
        .trim()
        .toLowerCase()
        .replace(/\s/g, "-");
    }
  },
  computed: {
    username() {
      return this.$store.getters["main/username"];
    }
  }
};
</script>

<style scoped>
.v-list {
  background-color: #fdfdfd;
}
</style>