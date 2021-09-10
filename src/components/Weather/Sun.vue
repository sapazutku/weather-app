<template>
  <div class="weather-sun">
    <div class="sun">
      <div class="rays"></div>
      <div class="rays"></div>
      <div class="rays"></div>
      <div class="rays"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.weather-sun {
  width: 100px;
  height: 100px;
  display: inline-block;
  position: relative;
}

.sun {
  width: 100px;
  height: 100px;
  background: linear-gradient(45deg, #f3a966, yellow);
  border-radius: 70%;
  transform: rotate(0deg);
  animation: xuanzhuang 12s infinite linear;
  margin-left: 60%;
  margin-right: auto;
  margin-top: 30%;
}

.rays {
  width: 8px;
  height: 15px;
  background: yellow;
  position: absolute;
  transform: translateX(-50%);
  left: 50%;
  top: -25px;
  box-shadow: 0 135px yellow;
  border-radius: 4px;
  transform-origin: 0px 75px;
}

.rays:nth-child(2) {
  transform: rotate(45deg);
}

.rays:nth-child(3) {
  transform: rotate(90deg);
}

.rays:nth-child(4) {
  transform: rotate(135deg);
}

@keyframes xuanzhuang {
  100% {
    transform: rotate(360deg);
  }
}

@keyframes Rotate {
  100% {
    transform: rotate(360deg);
  }
}

.weather-cloudAndSun .sun {
  position: absolute;
  left: 180px;
  top: 60px;
  z-index: 0;
}
</style>