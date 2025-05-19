<template>
  <LandingPage />
</template>

<script lang="ts" setup>
import LandingPage from "./src/landing-page.vue";

const setWindowFontSize = function (targetWidth: number) {
  const clientWidth = document.documentElement.clientWidth;
  console.log("clientWidth: ", clientWidth, "; psdWidth: ", targetWidth);
  if (clientWidth >= targetWidth) {
    document.documentElement.style.fontSize = "10px";
  } else {
    console.log("innerWidth: ", innerWidth);
    document.documentElement.style.fontSize =
      innerWidth / (targetWidth * 0.08) + "px";
    window.addEventListener(
      "resize",
      function () {
        document.documentElement.style.fontSize =
          innerWidth / (targetWidth * 0.08) + "px";
      },
      false
    );
  }
};

onMounted(() => {
  setWindowFontSize(1920);
});
</script>
