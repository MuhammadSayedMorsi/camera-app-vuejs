<template>
  <div id="app">
    <Camera v-on:takePicture="this.takePicture" />
    <Picture />
  </div>
</template>

<script>
import Camera from "./components/Camera";
import Picture from "./components/Picture";
export default {
  name: "App",
  components: {
    Camera,
    Picture
  },
  methods: {
    takePicture() {
      let ratio = window.innerHeight < window.innerWidth ? 16 / 9 : 9 / 16;
      const picture = document.querySelector("canvas");
      picture.width = window.innerWidth < 1280 ? window.innerWidth : 1280;
      picture.height = window.innerWidth / ratio;
      const ctx = picture.getContext("2d");
      ctx.imageSmoothingEnabled = true;
      ctx.imageSmoothingQuality = "heigh";
      ctx.drawImage(
        document.querySelector("video"),
        0,
        0,
        picture.width,
        picture.height
      );
    }
  }
};
</script>

<style>
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
