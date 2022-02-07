<template>
  <div class="grid">
    <div class="asideGameDiv">
      <v-img class="game-img" :src="gameCards.asideCard.src" width="150px" />
    </div>
    <div class="container-rows">
      <div
        class="gameDiv"
        v-for="(cards, index) in gameCards.commomCards"
        :key="index"
        :index="index"
      >
        <v-img class="game-img" :src="cards.src" width="150px">
          <div class="inside-card">
            <v-img :src="imgBarra">
              <div class="subtitle">
                <span class="money" style="margin-left: 10px"> $ </span>
                <span>{{ formatValues(cards.value) }}</span>
                <span class="money">,00</span>
              </div>
            </v-img>
          </div>
        </v-img>
      </div>
    </div>
  </div>
</template>
<script>
import imgBarra from "../../assets/Archive/barra_jackpot.png";

export default {
  name: "Lobby",
  data: function () {
    return {
      imgBarra,
    };
  },
  props: ["gameCards"],
  methods: {
    formatValues: function (value) {
      return value.split(",")[0];
    },
  },
};
</script>

<style scoped>
.grid {
  display: grid;
  margin-top: 2rem;
  justify-content: center;
  grid-template-columns: 150px 480px;
  gap: 15px;
}

.asideGameDiv {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background: black;
  border: 3px solid #ffd700;
  border-radius: 8px;
}

.container-rows {
  display: grid;
  height: 315px;
  gap: 15px 15px;
  grid-template-columns: repeat(3, 150px);
}

.game-img {
  border-radius: 6px;
}

.gameDiv {
  width: 150px;
  height: 150px;
  /* border: 3px solid #ffd700; */
  background: #ffd700;
  border-radius: 8px;
  padding: 3px;
}

.inside-card {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: flex-end;
}

span {
  color: #ffd700;
  font-family: "Poppins", "Arial", sans-serif;
  font-size: 16px;
  font-weight: 600;
}
.money {
  font-size: 12px;
}

.subtitle {
  margin-left: 1.1rem;
}

.asideGameDiv:hover,
.gameDiv:hover {
  animation: expand 3s;
}

@keyframes expand {
  from,
  to {
    transform: scale(1.1);
  }
}
</style>
