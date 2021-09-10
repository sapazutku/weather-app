<template>
  <div class="weather-snow">
    <div class="snow">
      <div class="f"></div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.weather-snow {
  width: 100px;
  height: 100px;
  display: inline-block;
  position: relative;
}

.snow {
  width: 150px;
  height: 10px;
  border-radius: 5px;
  background: #cdedf8;
  transform: rotate(0deg);
  position: absolute;
  top: 70%;
  left: 10%;
  animation: Rotate 12s infinite linear;
  position: relative;
}

.snow::after,
.snow::before {
  content: "";
  width: 150px;
  height: 10px;
  border-radius: 5px;
  background: #cdedf8;
  position: absolute;
}

.snow::after {
  transform: rotate(60deg);
}

.snow::before {
  transform: rotate(120deg);
}

.f {
  width: 28px;
  height: 10px;
  border-radius: 5px;
  position: absolute;
  background: #cdedf8;
  top: -45px;
  left: 25px;
  box-shadow: 0px 90px #cdedf8, 72px 90px #cdedf8, 72px 0px #cdedf8;
}

.f::after,
.f::before {
  content: "";
  width: 28px;
  height: 10px;
  transform: rotate(60deg);
  border-radius: 5px;
  position: absolute;
  background: #cdedf8;
  top: -10px;
  left: 55px;
  box-shadow: 0px 90px #cdedf8, 72px 90px #cdedf8, 72px 0px #cdedf8;
}

.f::before {
  transform: rotate(120deg);
  left: 15px;
  box-shadow: 72px 0px #cdedf8, 72px -90px #cdedf8, 0px -90px #cdedf8;
}

@keyframes Rotate {
  100% {
    transform: rotate(360deg);
  }
}
</style>