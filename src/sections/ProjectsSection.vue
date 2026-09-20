<script setup lang="ts">
import type { Language } from "../App.vue";
import SectionTitle from "../components/SectionTitle.vue";
defineProps<{ language: Language }>();
</script>

<template>
  <section id="projects" class="section projects-section grid-section">
    <div class="interactive-grid"></div>
    <div class="grid-vignette"></div>

    <div class="section-inner center-content">
      <SectionTitle :language="language" zh="项目" en="Projects" />
      <p class="project-empty">
        {{ language === "zh" ? "暂无。" : "Nothing here yet." }}
      </p>
    </div>
  </section>
</template>