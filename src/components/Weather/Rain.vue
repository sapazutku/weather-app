<template>
  <div class="weather-rain">
    <div class="cloud"></div>
    <div class="rain"></div>
    <div class="rain"></div>
    <div class="rain"></div>
    <div class="rain"></div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.weather-rain {
  width: 100px;
  height: 100px;
  position: relative;
  margin-left: 15px;
}

.cloud {
  border-radius: 25px;
  position: absolute;
  top: 40%;
  width: 140px;
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

.weather-cloudAndSun .cloud {
  z-index: 1;
  opacity: 0.95;
}

.weather-cloudAndSun .sun {
  position: absolute;
  left: 180px;
  top: 60px;
  z-index: 0;
}

.rain {
  width: 8px;
  height: 40px;
  background: linear-gradient(transparent, lightblue);
  position: absolute;
  left: 100%;
  top: 100%;
  border-radius: 2px;
  animation: rainning 2s infinite;
}

.rain:nth-child(2) {
  height: 20px;
  left: 60%;
  top: 100%;
}

.rain:nth-child(3) {
  height: 50px;
  left: 40%;
  top: 100px;
}

.rain:nth-child(4) {
  height: 25px;
  left: 80%;
  top: 100px;
}

@keyframes rainning {
  100% {
    top: 200px;
  }
}
</style>