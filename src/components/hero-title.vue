<template>
  <div class="hero-title">
    <span class="background" />
    <span class="title-shadow"><slot /></span>
    <span class="title"><slot /></span>
  </div>
</template>

<style>
.hero-title {
  position: relative;
  display: inline-block;
  color: orange;
  font-size: 6rem;
  line-height: 1;
  letter-spacing: -2px;
  text-transform: uppercase;
  transform: rotate(-4deg);
}

.hero-title .background {
  content: "";
  position: absolute;
  width: calc(100% + 2rem);
  height: calc(100% + 5rem);
  background: linear-gradient(to right, #e00, #f90);
  z-index: 0;
  transform: skewX(-20deg) rotate(-5deg) translate(-1.5rem, -2rem);
  border-radius: 2rem;
}

.hero-title .title-shadow {
  position: relative;
  z-index: 1;
  margin: 0;
  padding: 0 10px;
  display: inline-block;
  text-shadow: 0px 7px #000, 0px 10px 10px rgba(0, 0, 0, 0.5);
}

.hero-title .title {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  margin: 0;
  padding: 0 10px;
  display: inline-block;
  background: linear-gradient(to right, orange 0%, white 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
