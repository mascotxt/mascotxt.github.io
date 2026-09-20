<script setup lang="ts">
import type { Language } from "../App.vue";
import SectionTitle from "../components/SectionTitle.vue";
defineProps<{ language: Language }>();
</script>

<template>
  <section id="about" class="section about-section silk-section">
    <div class="silk-lines"></div>
    <div class="silk-glow"></div>

    <div class="section-inner about-inner">
      <SectionTitle :language="language" zh="关于我" en="About me" />

      <div class="about-copy">
        <p class="about-lead">
          {{ language === "zh" ? "我是彭子懿。" : "I'm Peng Ziyi." }}
        </p>

        <p>
          {{
            language === "zh"
              ? "目前就读于天津大学香港理工大学深圳未来技术学院。"
              : "Currently studying at the Tianjin University–The Hong Kong Polytechnic University Shenzhen Institute of Future Technology."
          }}
        </p>

        <p>
          {{
            language === "zh"
              ? "兴趣广泛，喜欢探索不同领域，也爱听音乐。"
              : "I have broad interests, enjoy exploring different fields, and love listening to music."
          }}
        </p>
      </div>
    </div>
  </section>
</template>