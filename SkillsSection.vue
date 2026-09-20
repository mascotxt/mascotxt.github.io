<script setup lang="ts">
import type { Language } from "../App.vue";
import SectionTitle from "../components/SectionTitle.vue";
defineProps<{ language: Language }>();
</script>

<template>
  <section id="skills" class="section skills-section pattern-section">
    <div class="dot-field"></div>
    <div class="dot-glow"></div>

    <div class="section-inner center-content">
      <SectionTitle :language="language" zh="技能" en="Skills" />
      <p class="minimal-statement">
        {{ language === "zh" ? "很杂，不作列举。" : "A little bit of everything." }}
      </p>
    </div>
  </section>
</template>