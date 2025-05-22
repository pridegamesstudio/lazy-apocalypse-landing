<template>
  <div class="background">
    <div class="cover">
      <div class="logo" />

      <div class="title" />

      <div class="stores">
        <a class="store store_apple" :href="oneLinkURL" target="_blank" />
        <a class="store store_google" :href="oneLinkURL" target="_blank" />
      </div>
    </div>

    <div class="gift">
      <div class="promocode">
        <span class="promocode-title">Welcome Gift Code: </span>
        <span class="promocode-code" @click="copyCode">{{ code }}</span>
        <div v-if="copied" class="copied-notice">Copied to clipboard!</div>
      </div>
    </div>

    <div class="about">
      <div class="about__text">
        Prepare for an action-packed idle tower defense adventure in Lazy
        Apocalypse: Tower Defense!
        <br />
        <br />
        Defend against relentless waves of zombies, upgrade your weapons, and
        become the most famous monster-slaying streamer in this
      </div>
    </div>

    <div class="gameplay">
      <div class="gameplay__heading" />

      <div class="gameplay__slider">
        <Swiper
          :slides-per-view="isMobile ? 1 : 3"
          :centered-slides="true"
          :loop="true"
          :lazy="true"
          :space-between="30"
          class="swiper"
          @swiper="onSwiper"
        >
          <SwiperSlide>
            <img
              class="gameplay__screenshot"
              src="./assets/screenshot-1.webp"
              alt=""
            />
          </SwiperSlide>
          <SwiperSlide>
            <img
              class="gameplay__screenshot"
              src="./assets/screenshot-2.webp"
              alt=""
            />
          </SwiperSlide>
          <SwiperSlide>
            <img
              class="gameplay__screenshot"
              src="./assets/screenshot-3.webp"
              alt=""
            />
          </SwiperSlide>
          <SwiperSlide>
            <img
              class="gameplay__screenshot"
              src="./assets/screenshot-4.webp"
              alt=""
            />
          </SwiperSlide>
          <SwiperSlide>
            <img
              class="gameplay__screenshot"
              src="./assets/screenshot-5.webp"
              alt=""
            />
          </SwiperSlide>
        </Swiper>
        <div class="swiper-prev-button" @click="prevSlide" />
        <div class="swiper-next-button" @click="nextSlide" />
        <div class="slider-border-bottom-left" />
        <div class="slider-border-top-right" />
      </div>
    </div>

    <div class="heroes">
      <div class="heroes__heading" />
      <div class="heroes__all" />
      <div class="heroes__text">
        <span>
          Never has fighting the zombie apocalypse been so much fun!
          <br />
          <br />
          Download lazy apocalypse and battle without leaving your chair!
        </span>
      </div>
    </div>

    <div class="end-stores">
      <div class="stores">
        <a class="store store_apple" :href="oneLinkURL" target="_blank" />
        <a class="store store_google" :href="oneLinkURL" target="_blank" />
      </div>
    </div>
  </div>

  <div class="footer">
    Copyright @ ITPINI OU. All Rights Reserved.
    <br />
    <a target="_blank" href="https://itpini.com/terms.php">
      [ Terms of Service ]
    </a>
    —
    <a target="_blank" href="https://itpini.com/privacy.php">
      [ Privacy Policy ]
    </a>
    <br />
    Email: <a href="mailto://help@itpini.org">help@itpini.org</a>
  </div>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import { ref } from "vue";
import { settings } from "./settings";

useHead({
  title: "Lazy Apocalypse: Tower Defense!",
});

const code = ref("Lazy1");
const copied = ref(false);

function copyCode() {
  navigator.clipboard
    .writeText(code.value)
    .then(() => {
      copied.value = true;
      setTimeout(() => (copied.value = false), 2000); // Сбросить уведомление через 2 секунды
    })
    .catch(() => {
      alert("Failed to copy!");
    });
}

const swiperRef = ref(null);

const onSwiper = (swiper) => {
  swiperRef.value = swiper;
};

const prevSlide = () => {
  swiperRef.value?.slidePrev(300);
};

const nextSlide = () => {
  swiperRef.value?.slideNext(300);
};

const userAgent = typeof navigator !== "undefined" ? navigator.userAgent : "";

const isMobile = computed(() =>
  /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
    userAgent
  )
);

const setupOneLink = () => {
  if (window.AF_SMART_SCRIPT?.generateOneLinkURL) {
    const oneLinkURL = `${settings.oneLinkURL}`;
    const webReferrer = "af_sub3";
    const mediaSource = { keys: ["utm_source"], defaultValue: "any_source" };
    const campaign = {
      keys: ["utm_campaign"],
      defaultValue: "any_campaign_name",
    };
    const adSet = { keys: ["utm_adset"], defaultValue: "any_ad_name" };
    const ad = { keys: ["utm_ad"], defaultValue: "any_ad_name" };
    const channel = { keys: ["utm_medium"], defaultValue: "any_channel_name" };
    const googleClickIdKey = "af_sub1";
    const afSub2 = { keys: ["fbclid"] };
    const custom_ss_ui = { paramKey: "af_ss_ui", defaultValue: "true" };

    //Call the function after embedding the code through a global parameter on the window object called window.AF_SMART_SCRIPT.
    //Onelink URL is generated.
    return window.AF_SMART_SCRIPT?.generateOneLinkURL({
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
        afCustom: [custom_ss_ui],
      },
    })?.clickURL;

    // If needed, you can download the script from: https://onelinksmartscript.appsflyer.com/onelink-smart-script-latest.js

    // See an example of implementation and how to place the URL result behind a CTA on your website: https://appsflyersdk.github.io/appsflyer-onelink-smart-script/examples/utm_parameters.html?utm_campaign=mycmpn&utm_source=mysource

    // See an example of how to display a QR code: https://appsflyersdk.github.io/appsflyer-onelink-smart-script/examples/qr_code.html?inmedia=my_email&incmp=my_campaign
  } else {
    setTimeout(setupOneLink, 500);
  }
};

const oneLinkURL = ref("");
onMounted(() => {
  oneLinkURL.value = setupOneLink();
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Bungee:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Bungee", Arial, Helvetica, sans-serif;
  font-weight: 700;
  font-size: 2.4px;
  background-color: #161a2b;
  color: #fff;
}
.__nuxt,
html,
body {
  overflow-x: hidden;
  background-image: url(./assets/background.webp);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center 1000px;
}

.background {
  position: relative;
  max-width: 1920px;
  margin: auto;
}

/* >>> START DESCRIPT */
.logo {
  position: absolute;
  top: 0;
  left: 0;
  width: 300px;
  height: 150px;
  margin: 40px;
  background-image: url(./assets/logo.webp);
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}

.cover {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: auto;
  flex-direction: column;
  background-image: url(./assets/cover.webp);
  background-size: cover;
  background-position: top center;
  background-repeat: no-repeat;
  height: 1000px;
}
.title {
  align-self: center;
  width: 100%;
  height: 140px;
  margin-bottom: 40px;
  margin-top: 500px;
  background-image: url(./assets/title.webp);
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}

.stores {
  display: inline-flex;
  width: max-content;
  align-self: center;
  justify-content: center;
  gap: 40px;
  padding: 10px 20px;
}

.store {
  width: calc(30px * 8);
  height: calc(10px * 8);
  cursor: pointer;
  text-decoration: none;
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}
.store_google {
  background-image: url(./assets/google.svg);
}

.store_apple {
  background-image: url(./assets/apple.svg);
}

.store:hover {
  opacity: 0.8;
}
/* <<< END DESCRIPT */

/* >>> START GIFT */
.gift {
  position: relative;
  align-self: center;
  height: 400px;
  background-image: url(./assets/gift.webp);
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  margin-bottom: 40px;
}

.promocode {
  position: absolute;
  top: 110px;
  left: 0;
  right: 0;
  margin: auto;
  text-align: center;
  font-size: 50px;
}

.promocode-title {
  color: #4600ac;
}

.promocode-code {
  color: #a33011;
  cursor: pointer;
}
.promocode-code:hover {
  color: #c34f2f;
}

.copied-notice {
  position: absolute;
  max-width: max-content;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  font-size: 52px;
  color: #4600ac;
  font-weight: 700;
  background: #fff;
  padding: 10px 80px;
  border-radius: 30px;
  box-shadow: 0px 0px 20px #000;
}
/* <<< END GIFT */

/* >>> START ABOUT */
.about {
  display: flex;
  justify-content: center;
  background-image: url(./assets/about.webp);
  height: max-content;
  height: 790px;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: top center;
}
.about__text {
  text-align: center;
  font-size: 30px;
  margin-top: 13%;
  line-height: 35px;
  color: #4c2e6c;
  font-weight: 400;
  transform: rotate(-3deg);
  width: 50%;
}
/* <<< END ABOUT */

/* >>> START GAMEPLAY */
.gameplay {
  margin-bottom: -200px;
}
.gameplay__heading {
  background-image: url(./assets/gameplay-title.webp);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  height: 230px;
  margin-bottom: -200px;
}
.gameplay__slider {
  position: relative;
  width: 50%;
  margin: auto;
}
.gameplay__screenshot {
  width: 100%;
}

.gameplay .swiper-prev-button,
.gameplay .swiper-next-button {
  position: absolute;
  top: calc(50% - 130px);
  width: 200px;
  background-size: contain;
  height: 200px;
  z-index: 1;
  cursor: pointer;
  transition: all 0.2s;
}

.gameplay .swiper-prev-button {
  left: -50px;
  background-image: url(./assets/arrow-left.png);
}
.gameplay .swiper-next-button {
  right: -50px;
  background-image: url(./assets/arrow-right.png);
}

@media screen and (min-width: 900px) {
  .gameplay .swiper-slide {
    transition: all 0.3s;
    opacity: 0.7;
    padding-top: 460px !important;
    padding-bottom: 460px !important;
  }

  .gameplay .swiper-slide-active {
    transform: scale(2);
    opacity: 1;
    z-index: 1;
  }

  .gameplay .swiper-prev-button:hover,
  .gameplay .swiper-next-button:hover {
    transform: scale(1.1);
    transition: all 0.2s;
  }

  .slider-border-bottom-left {
    position: absolute;
    bottom: 200px;
    left: 40px;
    background-size: contain;
    width: 300px;
    z-index: 2;
    height: 300px;
    background-repeat: no-repeat;
    background-image: url(./assets/slider-border-bottom-left.webp);
  }
  .slider-border-top-right {
    position: absolute;
    top: 200px;
    right: -150px;
    background-size: contain;
    width: 300px;
    z-index: 0;
    height: 300px;
    background-repeat: no-repeat;
    background-image: url(./assets/slider-border-top-right.webp);
  }
}

/* <<< END GAMEPLAY */

/* >>> START EVOLVE HERO */
.heroes {
  margin-top: 100px;
}
.heroes__heading {
  background-image: url(./assets/heroes-title.webp);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  width: 100%;
  height: 230px;
}
.heroes__all {
  margin-top: -180px;
  background-image: url(./assets/heroes-all.webp);
  background-size: 100%;
  background-repeat: no-repeat;
  background-position: center center;
  height: 850px;
  width: 100%;
}
.heroes__text {
  margin-top: -230px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-image: url(./assets/heroes-text.webp);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  width: 100%;
  height: 680px;
  text-align: center;
  font-size: 40px;
  padding: 0 200px;
  padding-right: 400px;
  color: #4b2f6c;
}
.heroes__text span {
  transform: rotate(-2deg);
}
/* <<< END EVOLVE HERO */

.end-stores {
  display: flex;
  justify-content: center;
  padding: 100px 0;
}

.footer {
  padding: 100px;
  text-align: center;
  line-height: 60px;
  font-size: 30px;
  background-image: url(./assets/footer.webp);
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}

.footer a {
  text-decoration: none;
  color: inherit;
  border-bottom: 1px dashed orange;
  color: orange;
}

@media screen and (max-width: 900px) {
  .logo {
    width: 100px;
    height: 80px;
    top: 10px;
    left: 10px;
    right: 0;
    margin: 0;
  }

  .cover {
    width: 100%;
    height: 100vh;
    max-height: 400px;
  }

  .title {
    height: 80px;
    width: 90%;
    margin: 0;
    margin-top: 200px;
  }

  .stores {
    gap: 10px;
    padding: 0;
  }

  .store {
    width: 140px;
    max-width: calc(50vw - 20px);
    height: 60px;
  }

  .gift {
    /* height: ; */
    aspect-ratio: 16/9;
    width: 100%;
    height: auto;
    padding: 0px;
    margin-bottom: 0;
    margin-top: -50px;
  }

  .promocode {
    top: 35%;
    font-size: 20px;
  }

  .about {
    height: auto;
    aspect-ratio: 16/9;
    margin-bottom: -50px;
    margin-top: -20px;
  }
  .about__text {
    font-size: 400%;
    line-height: 1;
    margin-top: 8%;
  }

  .gameplay {
    margin-top: 30px;
    margin-bottom: 0;
  }
  .gameplay__heading {
    height: auto;
    aspect-ratio: 16 / 9;
    width: 70%;
    margin-left: auto;
    margin-right: auto;
    margin-top: -80px;
    margin-bottom: 20px;
  }

  .gameplay__slider {
    margin-top: -50px;
    width: auto;
  }

  .gameplay .swiper-slide {
    padding: 0;
  }

  .gameplay .swiper-prev-button,
  .gameplay .swiper-next-button {
    width: 50px;
    height: 50px;
    top: calc(50% - 25px);
  }

  .gameplay .swiper-prev-button {
    left: 0px;
  }
  .gameplay .swiper-next-button {
    right: 0px;
  }

  .slider-border-bottom-left {
    display: none;
  }
  .slider-border-top-right {
    display: none;
  }

  .heroes {
    margin-top: 0px;
  }

  .heroes__heading {
    aspect-ratio: 16/9;
    height: auto;
    margin-top: 0px;
    width: 70%;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 20px;
  }

  .heroes__all {
    aspect-ratio: 16 / 9;
    margin-top: -100px;
    margin-bottom: 120px;
    height: auto;
  }

  .heroes__text {
    height: auto;
    aspect-ratio: 16/9;
    padding: 0;
    font-size: 500%;
    line-height: 1;
    padding-right: 100px;
    padding-left: 40px;
  }

  .end-stores {
    margin-top: -10px;
    padding: 0px;
    padding-bottom: 30px;
  }

  .footer {
    font-size: 20px;
    line-height: 2;
    padding: 20px;
  }

  .copied-notice {
    font-size: 15px;
  }
}

@media screen and (max-width: 900px) and (orientation: landscape) {
  .gameplay__slider {
    width: 50vh;
  }

  .gameplay .swiper-prev-button {
    left: -30px;
  }

  .gameplay .swiper-next-button {
    right: -30px;
  }
}
</style>
