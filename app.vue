<template>
  <LandingPage />
</template>

<script lang="ts" setup>
import LandingPage from "./src/landing-page.vue";
import { settings } from "./src/settings";

useHead({
  script: [
    // GOOGLE
    {
      src: "https://www.googletagmanager.com/gtag/js?id=AW-17028356516",
      async: true,
    },
    {
      innerHTML: `
        <!-- Google tag (gtag.js) -->
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());

        gtag('config', 'AW-17028356516');
      `,
    },

    // APPSFLYER
    {
      src: "https://onelinksmartscript.appsflyer.com/onelink-smart-script-latest.js",
      async: true,
    },

    // FACEBOOK PIXEL
    {
      innerHTML: `<!-- Meta Pixel Code -->
        !function(f,b,e,v,n,t,s)
        {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
        n.callMethod.apply(n,arguments):n.queue.push(arguments)};
        if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
        n.queue=[];t=b.createElement(e);t.async=!0;
        t.src=v;s=b.getElementsByTagName(e)[0];
        s.parentNode.insertBefore(t,s)}(window, document,'script',
        'https://connect.facebook.net/en_US/fbevents.js');
        fbq('init', '1901983463581071');
        fbq('track', 'PageView');
        <!-- End Meta Pixel Code -->
      `,
      type: "text/javascript",
    },
  ],
  noscript: [
    {
      children: `<img height="1" width="1" style="display:none" src="https://www.facebook.com/tr?id=1901983463581071&ev=PageView&noscript=1" />`,
    },
  ],
  __dangerouslyDisableSanitizers: ["script"],
});

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
