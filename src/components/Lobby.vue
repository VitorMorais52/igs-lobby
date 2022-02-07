<template>
  <div class="lobby">
    <div class="container">
      <Header />
      <Main />
      <Footer />
    </div>
  </div>
</template>

<script>
import Header from "./Header.vue";
import Main from "./Main";
import Footer from "./Footer.vue";

export default {
  name: "Lobby",
  data: function () {
    return {
      onboarding: true,
    };
  },
  components: {
    Header,
    Footer,
    Main,
  },
  props: {},
};
</script>

<style scoped>
.lobby {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: -webkit-linear-gradient(rgb(56, 153, 243), #4a56ff);
}
.container {
  background: url("../assets/Archive/background.png");
  min-width: 1120px;
}
</style>
