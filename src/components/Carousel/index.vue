<template>
  <div>
    <div class="carousel-app">
      <carousel @next="next" @prev="prev">
        <carousel-slide
          v-for="(games, index) in arrGames"
          :key="index"
          :index="index"
          :visibleSlide="visibleSlide"
          :direction="direction"
        >
          <games-grid :gameCards="games" :direction="direction" />
        </carousel-slide>
      </carousel>
    </div>
    <nav>
      <div class="container-nav">
        <div
          @click="setPage(n)"
          class="nav-button"
          v-for="n in arrGamesLength"
          :key="n"
          :index="n"
        >
          <v-img
            transition="false"
            src="../../assets/Archive/pagination_off.png"
            height="50px"
          >
            <v-img transition="false" :src="selectedPage(n)" height="50px" />
          </v-img>
        </div>
      </div>
    </nav>
  </div>
</template>
<script>
import Carousel from "./Carousel.vue";
import CarouselSlide from "./CarouselSlide.vue";
import GamesGrid from "./GamesGrid.vue";
export default {
  name: "CarouselApp",
  data: function () {
    return {
      arrGames: [
        {
          asideCard: {
            src: require("../../assets/games_img/aside_game_1.jpg"),
          },
          commomCards: [
            {
              src: require("../../assets/games_img/game_1.jpg"),
              value: "123.000,00",
            },
            {
              src: require("../../assets/games_img/game_2.jpg"),
              value: "123.000,00",
            },
            {
              src: require("../../assets/games_img/game_3.jpg"),
              value: "123.000,00",
            },
            {
              src: require("../../assets/games_img/game_4.jpg"),
              value: "123.000,00",
            },
            {
              src: require("../../assets/games_img/game_5.jpg"),
              value: "123.000,00",
            },
            {
              src: require("../../assets/games_img/game_6.jpg"),
              value: "123.000,00",
            },
          ],
        },
        {
          asideCard: {
            src: require("../../assets/games_img/aside_game_2.jpg"),
            value: "aside",
          },
          commomCards: [
            {
              src: require("../../assets/games_img/game_7.jpg"),
              value: "54.000,00",
            },
            {
              src: require("../../assets/games_img/game_8.jpg"),
              value: "54.000,00",
            },
            {
              src: require("../../assets/games_img/game_9.jpg"),
              value: "54.000,00",
            },
            {
              src: require("../../assets/games_img/game_10.jpg"),
              value: "54.000,00",
            },
            {
              src: require("../../assets/games_img/game_11.jpg"),
              value: "54.000,00",
            },
            {
              src: require("../../assets/games_img/game_12.jpg"),
              value: "54.000,00",
            },
          ],
        },
      ],
      visibleSlide: 0,
      direction: "left",
      imgPageOn: require("../../assets/Archive/pagination_on.png"),
      imgPageOff: require("../../assets/Archive/pagination_off.png"),
    };
  },
  components: {
    Carousel,
    CarouselSlide,
    GamesGrid,
  },
  computed: {
    arrGamesLength() {
      return this.arrGames.length;
    },
  },
  methods: {
    next: function () {
      if (this.visibleSlide >= this.arrGamesLength - 1) {
        this.visibleSlide = 0;
      } else {
        this.visibleSlide++;
      }
      this.direction = "left";
    },
    prev: function () {
      if (this.visibleSlide <= 0) {
        this.visibleSlide = this.arrGamesLength - 1;
      } else {
        this.visibleSlide--;
      }
      this.direction = "right";
    },
    selectedPage: function (n) {
      if (n - 1 === this.visibleSlide) {
        return this.imgPageOn;
      } else {
        return false;
      }
    },
    setPage: function (n) {
      this.direction = n - 1 < this.visibleSlide ? "right" : "left";
      this.visibleSlide = n - 1;
    },
  },
  props: {},
};
</script>

<style scoped>
.carousel-app {
  display: flex;
  justify-content: center;
}
nav {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
.container-nav {
  display: flex;
  justify-content: space-around;
}
.nav-button {
  width: 40px;
  margin: 0 10px;
  cursor: pointer;
}
</style>
