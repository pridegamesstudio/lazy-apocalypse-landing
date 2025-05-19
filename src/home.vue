<template>
  <div class="descript">
    <div class="header">
      <div class="logo">logo</div>
    </div>

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

  <div class="section giftcodes">
    <div class="gift-title">Welcome Gift Code</div>
    <div class="gift-code" @click="copyCode">{{ code }}</div>
    <div v-if="copied" class="copied-notice">Copied to clipboard!</div>
  </div>

  <div class="section about">
    Prepare for an action-packed idle
    <br />
    tower defense adventure in Lazy Apocalypse: Tower Defense!
    <br />
    <br />
    Defend against relentless waves of zombies, upgrade your weapons, and become
    the most famous monster-slaying streamer in this thrilling idle defense
    game. <br />Whether you’re strategizing or relaxing, the action never stops!
    <br /><br />
    Can you withstand the ultimate apocalypse?
  </div>

  <div class="section features">
    <HeroTitle>Features</HeroTitle>

    <Swiper
      :slides-per-view="3"
      :space-between="5"
      :loop="true"
      :effect="'coverflow'"
      :grab-cursor="true"
      :centered-slides="true"
      :coverflow-effect="{
        rotate: 50,
        stretch: 0,
        depth: 100,
        modifier: 1,
        slideShadows: true,
      }"
      :modules="[EffectCoverflow]"
      class="swiper"
    >
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 1"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 2"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 3"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 4"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 5"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 6"
        />
      </SwiperSlide>
    </Swiper>
  </div>

  <div class="section heroes">
    <HeroTitle>Hero Information</HeroTitle>

    <Swiper
      :slides-per-view="3"
      :space-between="5"
      :loop="true"
      :effect="'coverflow'"
      :grab-cursor="true"
      :centered-slides="true"
      :coverflow-effect="{
        rotate: 50,
        stretch: 0,
        depth: 100,
        modifier: 1,
        slideShadows: true,
      }"
      :modules="[EffectCoverflow]"
      class="swiper"
    >
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 1"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 2"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 3"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 4"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 5"
        />
      </SwiperSlide>
      <SwiperSlide>
        <img
          class="feature-img"
          src="https://images.unsplash.com/photo-1726137569825-7535962addcd?q=80&w=1770&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
          alt="Slide 6"
        />
      </SwiperSlide>
    </Swiper>
  </div>

  <div class="section footer">
    Copyright @ ITPINI OU. All Rights Reserved. <br />
    <a target="_blank" href="https://itpini.com/terms.php"
      >[ Terms of Service ]</a
    >
    —
    <a target="_blank" href="https://itpini.com/privacy.php"
      >[ Privacy Policy ]</a
    >

    <br />
    Email: <a href="mailto://help@itpini.org">help@itpini.org</a>
  </div>
</template>

<script setup>
import HeroTitle from "./components/hero-title.vue";
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectCoverflow } from "swiper/modules";

// Import Swiper styles
import "swiper/css";

import { ref, watch } from "vue";

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
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Bungee:wght@400;700&display=swap");

html {
  font-family: "Bungee", Arial, Helvetica, sans-serif;
  font-weight: 700;
  font-size: 10px;
  background: radial-gradient(circle at 30% 30%, #2c003e, #0d0d25);
  color: #fff;
}

.descript {
  display: flex;
  flex-direction: column;
  margin-bottom: 10rem;
}

.logo {
  width: 14rem;
  height: 7rem;
  margin: 4rem;
  background: #000;
}

.stores {
  display: inline-flex;
  width: max-content;
  align-self: center;
  justify-content: center;
  gap: 2rem;
  margin-top: 1rem;
  padding: 1rem 2rem;
}

.store {
  width: calc(3rem * 8);
  height: calc(1rem * 8);
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

.section {
  padding: 4rem 20rem;
  text-align: center;
}

.about {
  font-size: 2.5rem;
  line-height: 3.5rem;
  font-weight: 400;
  padding: 10rem 20rem;
  text-shadow: 0px 3px 2px #000;
}

.features {
  padding: 4rem;
  margin-bottom: 10rem;
}

.swiper {
  margin-top: 10rem;
}

.feature-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.heroes {
  padding: 4rem;
}

.footer {
  text-align: center;
  line-height: 3rem;
  font-size: 1.5rem;
}

.footer a {
  text-decoration: none;
  color: inherit;
  border-bottom: 1px dashed orange;
  color: orange;
}

.section.giftcodes {
  max-width: 700px;
  margin: 80px auto;
  padding: 50px;
  border-radius: 30px;
  text-align: center;
  position: relative;
  transform: rotate(-1deg) scale(1.02);
}

.gift-title {
  font-size: 5rem;
  color: orange;
  margin-bottom: 30px;
  transform: rotate(-2deg);
  text-shadow: 0px 2px 5px #000;
}

.gift-code {
  cursor: pointer;
  font-size: 3.5rem;
  display: inline-block;
  padding: 25px 50px;
  color: #000;
  background: linear-gradient(145deg, #ffae00, #ff6a00);
  border: 6px solid #000;
  border-radius: 20px;
  box-shadow: 4px 4px 0 #000, 0 0 25px #fff, inset 0 0 10px #fff;
  cursor: pointer;
  transform: rotate(1.5deg);
  transition: all 0.2s ease-in-out;
  position: relative;
  animation: giftBounce 3s infinite;
}

@keyframes giftBounce {
  0%,
  100% {
    transform: rotate(1.5deg) scale(1);
  }
  50% {
    transform: rotate(-1.5deg) scale(1.05);
  }
}

.gift-code:hover {
  background: linear-gradient(145deg, #ffe100, #ff7b00);
  color: #111;
  box-shadow: 6px 6px 0 #000, 0 0 40px #ff6a00, inset 0 0 15px #fff;
  transform: rotate(-3deg) scale(1.1);
}

.copied-notice {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  opacity: 0;
  margin-top: 1rem;
  font-size: 3rem;
  color: orange;
  font-weight: 700;
  animation: fadeOut 1s;
}

@keyframes fadeOut {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>
