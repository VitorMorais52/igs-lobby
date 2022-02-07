<template>
  <header>
    <div class="container-header">
      <v-img :src="imgHeader">
        <div class="content-header">
          <div class="left">
            <div @click="setUser" class="icon">
              <v-img transition="false" :src="userExists" />
            </div>
            <div class="icon"><v-img :src="iconHelp" /></div>
          </div>
          <div class="mid">
            <span
              style="
                font-size: 18px;
                font-weight: 800;
                -webkit-text-stroke: 1px black;
              "
            >
              JACKSPOT</span
            >
            <div class="mid-text">
              <span class="money">$</span
              ><span style="-webkit-text-stroke: 1px black"> 12.800.000</span>
            </div>
          </div>
          <div class="right">
            <div class="right-text">
              <span class="money" style="margin-right: 1rem">$</span>
              <span v-if="this.showMoney" class="money">5.600,10</span>
              <div class="hidden-value" v-if="!this.showMoney" />
            </div>
            <div @click="toggleMoney" class="icon">
              <v-img transition="false" :src="iconEye" />
            </div>
          </div>
        </div>
      </v-img>
    </div>
  </header>
</template>
<script>
import imgHeader from "./../assets/Archive/header.png";
import iconLogout from "./../assets/Archive/logout_idle.png";
import iconUser from "./../assets/Archive/user_idle.png";
import iconHelp from "./../assets/Archive/help_idle.png";
import iconEyeOn from "./../assets/Archive/eye_idle.png";
import iconEyeOff from "./../assets/Archive/eye_off_idle.png";

export default {
  name: "Lobby",
  data: function () {
    return {
      imgHeader,
      iconEyeOn,
      iconEyeOff,
      iconHelp,
      iconLogout,
      iconUser,
      showMoney: false,
      user: false,
    };
  },
  computed: {
    iconEye: function () {
      return this.showMoney ? iconEyeOn : iconEyeOff;
    },
    userExists: function () {
      return this.user ? iconUser : iconLogout;
    },
  },
  methods: {
    toggleMoney: function () {
      this.showMoney = !this.showMoney;
    },
    setUser: function () {
      this.user = !this.user;
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@600;700;900&display=swap");

span {
  color: #ffd700;
  font-family: "Poppins", "Arial", sans-serif;

  font-size: 50px;
  font-weight: 600;
  background: -webkit-linear-gradient(#ffd700, #ffed00);
  background-clip: border-box;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.money {
  font-size: 20px;
}

.content-header {
  display: flex;
  height: 100%;

  justify-content: space-between;
  align-items: center;
  margin: 0px 38px;
}

.hidden-value {
  width: 82px;
  height: 2px;
  background-color: #ffd700;
  border-radius: 4px;
  margin-top: 0.8rem;
}

.left {
  display: flex;
  flex: 1;
  padding-bottom: 2rem;
}

.left > div:first-child {
  margin-right: 10px;
}

.mid {
  flex: 1;
  text-align: center;
}

.mid-text {
  display: flex;
  align-items: center;
  justify-content: center;
}

.right {
  display: flex;
  justify-content: flex-end;
  flex: 1;
  padding-bottom: 2rem;
}

.right-text {
  display: flex;
  padding-top: 0.4rem;
}

.right > div:first-child {
  margin-right: 1.5rem;
}

.icon {
  height: 40px;
  width: 40px;
  cursor: pointer;
}
</style>
