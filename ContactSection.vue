<script setup lang="ts">
import type { Language } from "../App.vue";
import SectionTitle from "../components/SectionTitle.vue";
defineProps<{ language: Language }>();
</script>

<template>
  <section id="contact" class="section contact-section">
    <div class="liquid-orb liquid-one"></div>
    <div class="liquid-orb liquid-two"></div>
    <div class="liquid-orb liquid-three"></div>

    <div class="section-inner contact-inner">
      <SectionTitle :language="language" zh="联系我" en="Contact" />

      <div class="contact-card glass-card">
        <a href="mailto:mascotxt@outlook.com" class="contact-row">
          <span class="contact-label">Email</span>
          <span class="contact-value">mascotxt@outlook.com</span>
          <span class="contact-arrow">↗</span>
        </a>

        <div class="contact-divider"></div>

        <div class="contact-row">
          <span class="contact-label">WeChat</span>
          <span class="contact-value">bao_ccccc3104</span>
          <button
            class="copy-button"
            @click="navigator.clipboard?.writeText('bao_ccccc3104')"
          >
            Copy
          </button>
        </div>
      </div>
    </div>
  </section>
</template>