<template>
  <footer>
    <v-img :src="imgFooter"></v-img>
  </footer>
</template>
<script>
import imgFooter from "./../assets/Archive/footer.png";
export default {
  name: "Lobby",
  data: function () {
    return {
      imgFooter,
    };
  },
  props: {},
};
</script>

<style scoped>
.container-footer {
  width: 100%;
  height: 180px;
}
</style>
