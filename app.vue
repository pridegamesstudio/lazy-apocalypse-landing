<template>
  <Home />
</template>

<script lang="ts" setup>
import Home from "./src/home.vue";

const setWindowFontSize = function (psdWidth) {
  const clientWidth = document.documentElement.clientWidth;
  console.log("clientWidth: ", clientWidth, "; psdWidth: ", psdWidth);
  if (clientWidth >= psdWidth) {
    document.documentElement.style.fontSize = "10px";
  } else {
    console.log("innerWidth: ", innerWidth);
    document.documentElement.style.fontSize =
      innerWidth / (psdWidth * 0.08) + "px";
    window.addEventListener(
      "resize",
      function () {
        document.documentElement.style.fontSize =
          innerWidth / (psdWidth * 0.08) + "px";
      },
      false
    );
  }
};

onMounted(() => {
  setWindowFontSize(1920);
});
</script>
