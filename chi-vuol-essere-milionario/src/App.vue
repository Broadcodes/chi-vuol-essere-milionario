<template>
  <div id="app">
    <div v-if="!this.play">
      <MenuIntroComponent @newGame="getValueNewGame" />
    </div>
    <div v-else style="height: 100vh; overflow-y: hidden;">
      <div v-if="!skipVideo">
        <div class="skip-btn" @click="skip">
          <i class="fa-solid fa-forward"></i>
          <h5>Skip</h5>
        </div>
        <video src="@/../public/video/Sigla.mp4" autoplay></video>
      </div>
      <div v-else>
        <SettingProfileUser />
      </div>

    </div>
  </div>
</template>

<script>
import MenuIntroComponent from "./components/MenuIntroComponent.vue";
import SettingProfileUser from "./components/SettingProfileUser.vue";

export default {
  name: 'App',
  data() {
    return {
      play: false,
      skipVideo: false,
    }
  },
  components: {
    MenuIntroComponent,
    SettingProfileUser,
  },
  methods: {
    getValueNewGame(value) {
      this.play = value;

      setTimeout(() => {
        this.skipVideo = true;
      }, 19000);
    },
    skip() {
      this.skipVideo = true;
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
}

body {
  font-family: sans-serif;
  position: relative;

  .skip-btn {
    position: absolute;
    z-index: 10;
    bottom: 50px;
    right: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: .5;
    cursor: pointer;

    i{
      color: #fff;
      font-size: 2rem;
      margin-right: 20px;
    }

    h5{
      color: #fff;
      font-size: 1.5rem;
    }

    &:hover{
      opacity: 1;
    }
  }

  video {
    width: 100%;
    height: 100vh;
    object-fit: cover;
  }


}
</style>
