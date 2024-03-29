<template>
  <div class="container_all">
    <div class="portrait" v-show="!this.orientation">
      <div class="portrait_content">
        <lottie-interactive
          class="rotate-phone"
          path="rotate-phone.json"
          autoplay
          loop
        />
        <p style="font-size: 18px; font-weight: bold; margin-bottom: -10px;">
          Please rotate your device
        </p>
        <p style="font-size: 12px; ">We support landscape mode only</p>
      </div>
    </div>
    <div class="landscape">
      <div style="position: absolute; z-index: 1200;" v-if="this.show_video">
        <video class="video_player" controls autoplay>
          <source
            v-if="$route.name == 'Animal Cell'"
            src="./assets/AnimalCell.mp4"
            type="video/mp4"
          />
          <source
            v-if="$route.name == 'Plant Cell'"
            src="./assets/PlantCell.mp4"
            type="video/mp4"
          />
          <source
            v-if="
              $route.name == 'Mitosis' ||
                'Prophase' ||
                'Anaphase' ||
                'Metaphase' ||
                'Telophase'
            "
            src="./assets/Mitosis.mp4"
            type="video/mp4"
          />
          Sorry, your browser doesn't support embedded videos.
        </video>
      </div>
      <div class="button_always_present">
        <button
          class="full_screen_button"
          @click="this.show_video = !this.show_video"
          v-show="this.orientation"
        >
          <p v-if="!this.show_video">Take a Guided Tour</p>
          <p v-else>Close Guided Tour</p>
        </button>
        <button
          class="full_screen_button_view"
          @click="fullScreenMode = !fullScreenMode"
        >
          <p v-if="!this.fullScreenMode">Enter Full Screen</p>
          <p v-else>Exit Full Screen</p>
        </button>
      </div>
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </div>
    <div class="back_trans">
      <lottie-interactive
        path="loader_trans.json"
        loop
        interaction="play-on-show"
        speed="1"
      />
      Loading to {{ $route.name }}
    </div>
  </div>
</template>

<script>
import { LottieInteractive } from "lottie-interactive";
export default {
  data() {
    return {
      loading: false,
      route: this.$route.name,
      orientation: true,
      fullScreenMode: false,
      show_video: false,
    };
  },
  components: {
    LottieInteractive,
  },
  watch: {
    $route(to, from) {
      this.toggle = false;
      console.log("Route changed from " + from.path + " to " + to.path);
      console.log(this.$route.name);
      const orientation = window.screen.orientation.type;
      console.log(orientation);
      if (orientation === "portrait-primary") {
        console.log("portarit");
        this.orientation = false;
      } else if (
        orientation === "landscape-primary" ||
        orientation === "landscape-secondary"
      ) {
        console.log("landscape");
        this.orientation = true;
      }
    },
    checkRoute() {
      console.log(this.$route.name);
    },
    checkOrientation() {
      this.handleOrientationChange();
    },
    fullScreenMode: function() {
      if (this.fullScreenMode == true) {
        this.openFullscreen();
      } else {
        this.closeFullscreen();
      }
    },
  },
  beforeUpdate() {
    console.log("I am updating");
  },
  mounted() {
    window.addEventListener("orientationchange", this.handleOrientationChange);
  },
  methods: {
    handleOrientationChange() {
      const orientation = window.screen.orientation.type;
      if (orientation === "portrait-primary") {
        console.log("portarit");
        this.orientation = false;
      } else if (orientation === "landscape-primary") {
        console.log("landscape");
        this.orientation = true;
      } else if (orientation === "landscape-secondary") {
        console.log("landscape");
        this.orientation = true;
      }
    },
    openFullscreen: function() {
      var elem = document.documentElement;
      if (elem.requestFullscreen) {
        elem.requestFullscreen();
      } else if (elem.mozRequestFullScreen) {
        elem.mozRequestFullScreen();
      } else if (elem.webkitRequestFullscreen) {
        elem.webkitRequestFullscreen();
      } else if (elem.msRequestFullscreen) {
        elem.msRequestFullscreen();
      }
    },

    closeFullscreen: function() {
      if (document.exitFullscreen) {
        document.exitFullscreen();
      } else if (document.mozCancelFullScreen) {
        document.mozCancelFullScreen();
      } else if (document.webkitExitFullscreen) {
        document.webkitExitFullscreen();
      } else if (document.msExitFullscreen) {
        document.msExitFullscreen();
      }
    },
  },
};
</script>

<style>
video::-webkit-media-controls-fullscreen-button {
  display: none;
}
.video_player {
  position: fixed;
  right: 0;
  bottom: 0;
  min-width: 100%;
  min-height: 100%;
}
.full_screen_button_view {
  border: none;
  border-radius: 15px;
  height: 50px;
  padding: 10px;
  display: flex;
  justify-items: center;
  align-items: center;
  cursor: pointer;
  font-weight: bold;
}
.full_screen_button {
  border: none;
  border-radius: 15px;
  height: 50px;
  padding: 10px;
  display: flex;
  justify-items: center;
  align-items: center;
  cursor: pointer;
  font-weight: bold;
}
.portrait {
  z-index: 1000;
  background-color: #030303;
  color: #fff;
  height: 100vh;
  width: 100%;
  position: absolute;
  top: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
.portrait_content {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.rotate-phone {
  width: 200px;
}
.back_trans {
  width: 100%;
  height: 100vh;
  background-color: #000;
  position: absolute;
  top: 0;
  z-index: -1;
  color: #ffff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.fade-leave-active {
  transition: opacity 2s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
::selection {
  color: none;
  background: none;
}
/* For Mozilla Firefox */
::-moz-selection {
  color: none;
  background: none;
}
@font-face {
  font-family: "Poppins";
  src: url(./assets/Poppins-Regular.ttf);
}
@font-face {
  font-family: "Bebas";
  src: url(./assets/BebasNeue-Regular.ttf);
}
html {
  -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
}
body {
  background: #000000;
  overflow: hidden;
}
button {
  font-family: Poppins;
}
#app {
  font-family: Poppins;
  -webkit-font-smoothing: antialiased;
  background: #000000;
}
.container_all {
  overflow: hidden;
  margin: 0 auto;
  background: #000000;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateX(2em);
}
.fade-enter-active,
fade-leave-active {
  transition: all 0.3s ease;
}
canvas {
  position: fixed;
  z-index: 0;
  background: #000000;
  top: 0;
  right: 0;
}
</style>
