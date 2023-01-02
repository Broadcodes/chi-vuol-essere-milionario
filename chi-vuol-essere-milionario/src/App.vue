<template>
  <div id="app">
    <div v-if="!this.play">
      <MenuIntroComponent @newGame="getValueNewGame" />
    </div>
    <div v-else>
      <div v-if="!skipVideo">
        <div class="skip-btn" @click="skip">
          <i class="fa-solid fa-forward">Skip</i>
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
}

video {
  width: 100%;
  height: 100vh;
  object-fit: cover;
}
</style>
