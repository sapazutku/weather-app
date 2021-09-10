<template>
  <div class="weather-cloud">
    <div class="cloud"></div>
    <div class="cloud"></div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.weather-cloud {
  width: 60px;
  height: 60px;
  display: inline-block;
  position: relative;
}

.cloud {
  border-radius: 25px;
  position: absolute;
  top: 70%;
  left: 50%;
  width: 150px;
  height: 50px;
  background: #cdedf8;
}

.cloud:nth-child(2) {
  left: 200px;
  width: 100px;
  height: 30px;
  background: #cdedf8;
  opacity: 1;
  animation: cloud 8s linear infinite;
}

.cloud::after,
.cloud::before {
  content: "";
  display: block;
  background: #cdedf8;
  border-radius: 50%;
  position: absolute;
}

.cloud:nth-child(2)::after,
.cloud:nth-child(2)::before {
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

.cloud:nth-child(2)::after {
  width: 50px;
  height: 50px;
  left: 35px;
  top: -30px;
}

.cloud:nth-child(2)::before {
  width: 40px;
  height: 40px;
  top: -10px;
  left: 0px;
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
</style>