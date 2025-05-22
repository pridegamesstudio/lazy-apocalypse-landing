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
    {
      innerHTML: `
        const setupOneLink = () => {
          if (window.AF_SMART_SCRIPT?.generateOneLinkURL) {
            var oneLinkURL = "${settings.oneLinkURL}";
            var webReferrer = "af_sub3";
            var mediaSource = {keys:["utm_source"],defaultValue:"any_source"};
            var campaign = {keys:["utm_campaign"],defaultValue:"any_campaign_name"};
            var adSet = {keys:["utm_adset"],defaultValue:"any_ad_name"};
            var ad = {keys:["utm_ad"],defaultValue:"any_ad_name"};
            var channel = {keys:["utm_medium"],defaultValue:"any_channel_name"};
            var googleClickIdKey = "af_sub1";
            var afSub2 = {keys:["fbclid"]};
            var custom_ss_ui = {paramKey:"af_ss_ui",defaultValue:"true"};

            //Call the function after embedding the code through a global parameter on the window object called window.AF_SMART_SCRIPT.
            //Onelink URL is generated.
            var result = window.AF_SMART_SCRIPT.generateOneLinkURL({
                oneLinkURL: oneLinkURL,
                webReferrer: webReferrer,
                afParameters: {
                    mediaSource: mediaSource,
                    campaign: campaign,
                    adSet: adSet,
                    ad: ad,
                    channel: channel,
                    googleClickIdKey: googleClickIdKey,
                    afSub2: afSub2,
                    afCustom: [
                        custom_ss_ui
                    ]
                }
            });


            // If needed, you can download the script from: https://onelinksmartscript.appsflyer.com/onelink-smart-script-latest.js

            // See an example of implementation and how to place the URL result behind a CTA on your website: https://appsflyersdk.github.io/appsflyer-onelink-smart-script/examples/utm_parameters.html?utm_campaign=mycmpn&utm_source=mysource

            // See an example of how to display a QR code: https://appsflyersdk.github.io/appsflyer-onelink-smart-script/examples/qr_code.html?inmedia=my_email&incmp=my_campaign
          } else {
            setTimeout(waitForAF, 500)
          };
        };

        setupOneLink();
      `,
      type: "text/javascript",
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
