<template>
  <LandingPage />
</template>

<script lang="ts" setup>
import LandingPage from "./src/landing-page.vue";
import { settings } from "./src/settings";

useHead({
  script: [
    // APPSFLYER
    {
      src: "https://onelinksmartscript.appsflyer.com/onelink-smart-script-latest.js",
      async: true,
    },
    {
      innerHTML: `
        const setupOneLink = () => {
          if (window.AF_SMART_SCRIPT?.generateOneLinkURL) {
            window.AF_SMART_SCRIPT.generateOneLinkURL({
              oneLinkURL: '${settings.oneLinkURL}',
              afParameters: {
                mediaSource: {
                  keys: ['utm_source', 'af_media_source'],
                  defaultValue: 'website'
                },
                campaign: {
                  keys: ['utm_campaign'],
                  defaultValue: 'default_campaign'
                },
                adSet: {
                  keys: ['utm_content', 'af_adset'],
                  defaultValue: 'general'
                }, // Группа объявлений
                ad: {
                  keys: ['utm_term', 'af_ad'],
                  defaultValue: 'none'
                }, // Ключевое слово/креатив
              }
            });
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
</script>
