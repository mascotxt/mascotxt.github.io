<script setup lang="ts">
import type { Language } from "../App.vue";

defineProps<{
  language: Language;
  zh: string;
  en: string;
  eyebrow?: string;
}>();
</script>

<template>
  <div class="section-heading">
    <div v-if="eyebrow" class="eyebrow">{{ eyebrow }}</div>
    <div class="title-line">
      <h2>{{ language === "zh" ? zh : en }}</h2>
      <span>{{ language === "zh" ? en : zh }}</span>
    </div>
  </div>
</template>