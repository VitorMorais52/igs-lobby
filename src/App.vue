<template>
  <v-app>
    <Lobby />
  </v-app>
</template>

<script>
import Lobby from "./components/Lobby.vue";

export default {
  name: "App",
  components: {
    Lobby,
  },
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
