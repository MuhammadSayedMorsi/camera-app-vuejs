<template>
  <div class="camera">
    <video autoplay class="feed"></video>
    <button class="snap" v-on:click="$emit('takePicture')">SNAP</button>
  </div>
</template>

<script>
export default {
  name: "camera",
  methods: {
    init() {
      let constraints = {
        video: {
          width: {
            min: 640,
            ideal: 1280,
            max: 1920
          },
          height: {
            min: 360,
            ideal: 720,
            max: 1080
          }
        }
      };
      if (
        "mediaDevices" in navigator &&
        "getUserMedia" in navigator.mediaDevices
      ) {
        navigator.mediaDevices.getUserMedia(constraints).then(stream => {
          const videoPlayer = document.querySelector("video");
          videoPlayer.srcObject = stream;
          videoPlayer.play();
        });
      }
    }
  },
  beforeMount() {
    this.init();
  }
};
</script>
<style lang="sass" scoped>
  .camera
    width: 100vw;
    height: 100vh;
    padding: 25px;
    .feed
      display: block;
      width: 100%;
      max-width: 700px;
      margin: 0 auto;
      box-shadow: 6px 6px 12px 0px rgba(0, 0, 0, 0.35);
      background-color: #171717;
    .snap
      display: block;
      width: 75px;
      height: 75px;
      border-radius: 50%;
      margin: 25px auto 0;
      background-color: transparentize($color: #ffce00, $amount: .75);
      border: 1px solid #171717;
      outline: none;

      &:hover
        background-color: #ffce00;
      &:active
        background-color: darken($color: #ffce00, $amount: 10);
</style>