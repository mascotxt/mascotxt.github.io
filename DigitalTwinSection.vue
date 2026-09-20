<script setup lang="ts">
import type { Language } from "../App.vue";
import SectionTitle from "../components/SectionTitle.vue";
import DigitalTwinChat from "../components/DigitalTwinChat.vue";
defineProps<{ language: Language }>();
</script>

<template>
  <section id="digital-twin" class="section twin-section">
    <div class="twin-grid"></div>

    <div class="section-inner twin-inner">
      <SectionTitle :language="language" zh="数字孪生" en="Digital Twin" />
      <p class="twin-description">
        {{
          language === "zh"
            ? "一个还在成长中的数字版本。"
            : "A digital version that is still evolving."
        }}
      </p>

      <DigitalTwinChat />
    </div>
  </section>
</template>