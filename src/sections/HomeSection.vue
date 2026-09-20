<script setup lang="ts">
import type { Language } from "../App.vue";
defineProps<{ language: Language }>();
</script>

<template>
  <section id="home" class="section home-section aurora-section">
    <div class="aurora-orb orb-one"></div>
    <div class="aurora-orb orb-two"></div>
    <div class="aurora-orb orb-three"></div>
    <div class="aurora-noise"></div>

    <div class="home-content reveal">
      <div class="home-face">^_^</div>
      <div class="home-hello">Hello</div>
      <p>{{ language === "zh" ? "请下滑来认识我……" : "Scroll down to meet me..." }}</p>
    </div>

    <div class="scroll-indicator">
      <span></span>
      <small>SCROLL</small>
    </div>
  </section>
</template>