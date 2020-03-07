<template>
  <div class="picture">
    <canvas></canvas>
  </div>
</template>

<style lang="sass" scoped>
  .picture
    display: block;
    width: 800px;
    height: 300px;
    margin: 0 auto 180px auto;
    padding: 25px;
    box-sizing: border-box;
    canvas
      display: block;
      width: 100%;
      margin: 0 auto;
      box-shadow: 4px 4px 12px 0px transparentize($color: #171717, $amount: 0.5)
</style>