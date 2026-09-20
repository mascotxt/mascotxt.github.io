<script setup lang="ts">
import { computed, ref } from "vue";
import Navigation from "./components/Navigation.vue";
import HomeSection from "./sections/HomeSection.vue";
import AboutSection from "./sections/AboutSection.vue";
import SkillsSection from "./sections/SkillsSection.vue";
import ProjectsSection from "./sections/ProjectsSection.vue";
import ContactSection from "./sections/ContactSection.vue";
import DigitalTwinSection from "./sections/DigitalTwinSection.vue";
import FeedbackSection from "./sections/FeedbackSection.vue";

export type Language = "zh" | "en";

const language = ref<Language>("zh");
const menuOpen = ref(false);

const navItems = computed(() => [
  { id: "home", zh: "首页", en: "Home" },
  { id: "about", zh: "关于我", en: "About me" },
  { id: "skills", zh: "技能", en: "Skills" },
  { id: "projects", zh: "项目", en: "Projects" },
  { id: "contact", zh: "联系我", en: "Contact" },
  { id: "digital-twin", zh: "数字孪生", en: "Digital Twin" },
  { id: "feedback", zh: "反馈", en: "Feedback" },
]);

function toggleLanguage() {
  language.value = language.value === "zh" ? "en" : "zh";
}

function scrollToSection(id: string) {
  menuOpen.value = false;
  document.getElementById(id)?.scrollIntoView({ behavior: "smooth" });
}
</script>

<template>
  <div class="site-shell" :class="{ 'menu-is-open': menuOpen }">
    <Navigation
      :language="language"
      :menu-open="menuOpen"
      :items="navItems"
      @toggle-language="toggleLanguage"
      @toggle-menu="menuOpen = !menuOpen"
      @navigate="scrollToSection"
    />

    <main>
      <HomeSection :language="language" />
      <AboutSection :language="language" />
      <SkillsSection :language="language" />
      <ProjectsSection :language="language" />
      <ContactSection :language="language" />
      <DigitalTwinSection :language="language" />
      <FeedbackSection :language="language" />
    </main>

    <footer class="site-footer">
      <span>🐙 Mascott</span>
      <span>© {{ new Date().getFullYear() }}</span>
    </footer>
  </div>
</template>