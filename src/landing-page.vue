<template>
  <div class="background">
    <div class="cover">
      <div class="logo" />

      <div class="title" />

      <div class="stores">
        <a
          class="store store_apple"
          href="https://apps.apple.com/us/app/lazy-apocalypse-tower-defense/id6742743519"
          target="_blank"
        />
        <a
          class="store store_google"
          href="https://play.google.com/store/apps/details?id=com.ZombieIdleDefenseChair&hl=en&gl=US"
          target="_blank"
        />
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
          :slides-per-view="3"
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
        <a
          class="store store_apple"
          href="https://apps.apple.com/us/app/lazy-apocalypse-tower-defense/id6742743519"
          target="_blank"
        />
        <a
          class="store store_google"
          href="https://play.google.com/store/apps/details?id=com.ZombieIdleDefenseChair&hl=en&gl=US"
          target="_blank"
        />
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
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Bungee:wght@400;700&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Bungee", Arial, Helvetica, sans-serif;
  font-weight: 700;
  font-size: 10px;
  background: radial-gradient(circle at 30% 30%, #2c003e, #0d0d25);
  color: #fff;
}
.__nuxt,
html,
body {
  overflow-x: hidden;
}

.background {
  background-image: url(./assets/background.webp);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center 50rem;
}

/* >>> START DESCRIPT */
.logo {
  position: absolute;
  top: 0;
  left: 0;
  width: 30rem;
  height: 15rem;
  margin: 4rem;
  background-image: url(./assets/logo.webp);
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}

.cover {
  display: flex;
  flex-direction: column;
  background-image: url(./assets/cover.webp);
  background-size: cover;
  background-position: top center;
  background-repeat: no-repeat;
  height: 100rem;
}
@media screen and (max-width: 900px) {
  .cover {
    margin-bottom: 10rem;
  }
}

.title {
  align-self: center;
  width: 80vw;
  height: 12rem;
  background-image: url(./assets/title.webp);
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  margin-top: 66rem;
  margin-bottom: 4rem;
}

.stores {
  display: inline-flex;
  width: max-content;
  align-self: center;
  justify-content: center;
  gap: 2rem;
  padding: 1rem 2rem;
}

.store {
  box-shadow: 0px 0px 10px #4600ac;
  width: calc(3rem * 8);
  height: calc(1rem * 8);
  cursor: pointer;
  text-decoration: none;
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}
@media screen and (max-width: 900px) {
  .store {
    width: calc(3rem * 16);
    height: calc(1rem * 16);
    border-radius: 4px;
  }
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
  width: 100vw;
  height: 40rem;
  background-image: url(./assets/gift.webp);
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  margin-bottom: 4rem;
}
@media screen and (max-width: 900px) {
  .gift {
    height: 50rem;
  }
}

.promocode {
  position: absolute;
  top: 11.5rem;
  left: 0;
  right: 0;
  margin: auto;
  text-align: center;
  font-size: 5rem;
}
@media screen and (max-width: 900px) {
  .promocode {
    font-size: 6rem;
    top: 14rem;
  }
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
  font-size: 5.2rem;
  color: #4600ac;
  font-weight: 700;
  background: #fff;
  padding: 1rem 8rem;
  border-radius: 3rem;
  box-shadow: 0px 0px 2rem #000;
}
/* <<< END GIFT */

/* >>> START ABOUT */
.about {
  display: flex;
  align-items: center;
  justify-content: center;
  background-image: url(./assets/about.webp);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: top center;
  width: 100vw;
  height: 64rem;
  padding: 0 38rem;
}
.about__text {
  text-align: center;
  font-size: 3rem;
  line-height: 3.5rem;
  color: #4c2e6c;
  font-weight: 400;
  transform: rotate(-3deg);
}
@media screen and (max-width: 900px) {
  .about__text {
    font-size: 4rem;
    line-height: 4rem;
  }
}
/* <<< END ABOUT */

/* >>> START GAMEPLAY */
.gameplay {
}
.gameplay__heading {
  background-image: url(./assets/gameplay-title.webp);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  width: 100vw;
  height: 33rem;
}
.gameplay__slider {
  position: relative;
  width: 90vw;
  margin: auto;
}
.gameplay__screenshot {
  width: 100%;
  height: fit-content;
}

.gameplay .swiper-slide {
  transition: all 0.3s;
  opacity: 0.7;
  padding-top: 36rem !important;
  padding-bottom: 36rem !important;
}

.gameplay .swiper-slide-active {
  transform: scale(2);
  opacity: 1;
  z-index: 1;
}

.gameplay .swiper-prev-button,
.gameplay .swiper-next-button {
  position: absolute;
  top: calc(50% - 13rem);
  width: 20rem;
  background-size: contain;
  height: 20rem;
  z-index: 1;
  cursor: pointer;
  transition: all 0.2s;
}
.gameplay .swiper-prev-button:hover,
.gameplay .swiper-next-button:hover {
  transform: scale(1.1);
  transition: all 0.2s;
}

.gameplay .swiper-prev-button {
  left: -5rem;
  background-image: url(./assets/arrow-left.png);
}
.gameplay .swiper-next-button {
  right: -5rem;
  background-image: url(./assets/arrow-right.png);
}

.slider-border-bottom-left {
  position: absolute;
  bottom: 7rem;
  left: -5rem;
  background-size: contain;
  width: 50rem;
  z-index: 2;
  height: 50rem;
  background-repeat: no-repeat;
  background-image: url(./assets/slider-border-bottom-left.webp);
}
.slider-border-top-right {
  position: absolute;
  top: 0.8rem;
  right: -20rem;
  background-size: contain;
  width: 40rem;
  z-index: 0;
  height: 40rem;
  background-repeat: no-repeat;
  background-image: url(./assets/slider-border-top-right.webp);
}
/* <<< END GAMEPLAY */

/* >>> START EVOLVE HERO */
.heroes {
  margin-top: 10rem;
}
.heroes__heading {
  background-image: url(./assets/heroes-title.webp);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  width: 100vw;
  height: 33rem;
}
.heroes__all {
  margin-top: -10rem;
  background-image: url(./assets/heroes-all.webp);
  background-size: 110%;
  background-repeat: no-repeat;
  background-position: center center;
  height: 67rem;
  width: 100vw;
}
.heroes__text {
  margin-top: -18rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-image: url(./assets/heroes-text.webp);
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center center;
  width: 100vw;
  height: 54rem;
  text-align: center;
  font-size: 4rem;
  padding: 0 20rem;
  padding-right: 40rem;
  color: #4b2f6c;
}
.heroes__text span {
  transform: rotate(-2deg);
}
/* <<< END EVOLVE HERO */

.end-stores {
  display: flex;
  justify-content: center;
  padding: 10rem 0;
}

.footer {
  padding: 10rem;
  text-align: center;
  line-height: 6rem;
  font-size: 3rem;
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
</style>
