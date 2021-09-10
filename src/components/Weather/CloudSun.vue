<template>
  <div class="weather-cloudAndSun">
    <div class="cloud"></div>
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
.weather-cloudAndSun {
  width: 100px;
  height: 100px;
  display: inline-block;
  position: relative;
}

.sun {
  width: 100px;
  height: 100px;
  background: linear-gradient(45deg, #f3a966, yellow);
  border-radius: 100%;
  transform: rotate(0deg);
  animation: xuanzhuang 12s infinite linear;
  position: absolute;
  left: 50%;
  top: 50%;
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

.cloud {
  border-radius: 25px;
  position: absolute;
  top: 80%;
  width: 150px;
  height: 50px;
  background: #cdedf8;
}

.cloud::after,
.cloud::before {
  content: "";
  display: block;
  background: #cdedf8;
  border-radius: 50%;
  position: absolute;
}

.cloud::after {
  width: 80px;
  height: 80px;
  left: 45px;
  top: -45px;
}

.cloud::before {
  width: 60px;
  height: 60px;
  top: -10px;
  left: 0;
}

@keyframes cloud {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: scale(0.8) translateX(-200%);
  }
}

@keyframes Rotate {
  100% {
    transform: rotate(360deg);
  }
}

.weather-cloudAndSun .cloud {
  z-index: 1;
  opacity: 0.95;
}

.weather-cloudAndSun .sun {
  position: absolute;
  margin-left: 1px;
  margin-top: 1%;
  top: 10%;
  z-index: 0;
}
</style>