<template>
  <section class="masthead" role="img" aria-label="Image Description">
    <div class="hero-container">
      <h1>Jan's <br />Portfolio <br />Page</h1>
      <AppIphone />
    </div>
    <canvas id="canvas" width="32px" height="32px"> </canvas>
  </section>
</template>

<script></script>

<style scoped>
.hero-container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: row;
  flex-wrap: wrap;

  /* text-align: left; */
}
#canvas {
  background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
  background-size: 400% 400%;
  animation: gradient 20s ease infinite;
  width: 100%;
  height: 100%;
  transform: skewY(-11deg);
  position: absolute;
  top: -360px;
}

@keyframes gradient {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.masthead {
  /* display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: column;
  text-align: left; */
  width: 100%;
  height: 100vh; /* if you don't want it to take up the full screen, reduce this number */

  /* overflow: hidden;
  background-size: cover !important;
  background-color: blue; */
}
h1 {
  z-index: 9999;
  opacity: 0.6;
  font-style: normal;
  font-weight: bold;
  font-size: 11vmin;
  letter-spacing: 0.03em;
  line-height: 1;
  margin-bottom: 1px;
}
</style>
