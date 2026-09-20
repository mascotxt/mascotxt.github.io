<script setup lang="ts">
import { ref } from "vue";
import type { Language } from "../App.vue";
import SectionTitle from "../components/SectionTitle.vue";
import FeedbackModal from "../components/FeedbackModal.vue";

defineProps<{ language: Language }>();
const open = ref(false);
</script>

<template>
  <section id="feedback" class="section feedback-section">
    <div class="ripple-layer">
      <span v-for="n in 7" :key="n" :style="{ '--i': n }"></span>
    </div>

    <div class="section-inner feedback-inner">
      <SectionTitle :language="language" zh="反馈" en="Feedback" />

      <button class="feedback-orb" @click="open = true">
        <strong>{{ language === "zh" ? "点我反馈" : "Feedback" }}</strong>
        <span>{{ language === "zh" ? "Feedback" : "点我反馈" }}</span>
      </button>
    </div>

    <FeedbackModal :open="open" @close="open = false" />
  </section>
</template>