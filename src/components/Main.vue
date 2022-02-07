<template>
  <main>
    <div class="container-main">
      <Carousel />
    </div>
  </main>
</template>
<script>
import Carousel from "./Carousel";

export default {
  name: "Lobby",
  data: function () {
    return {};
  },
  components: {
    Carousel,
  },
  props: {},
};
</script>

<style scoped>
.container-main {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
