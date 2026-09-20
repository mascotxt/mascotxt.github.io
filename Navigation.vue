<script setup lang="ts">
import type { Language } from "../App.vue";

interface NavItem {
  id: string;
  zh: string;
  en: string;
}

defineProps<{
  language: Language;
  menuOpen: boolean;
  items: NavItem[];
}>();

const emit = defineEmits<{
  "toggle-language": [];
  "toggle-menu": [];
  navigate: [id: string];
}>();
</script>

<template>
  <header class="navigation">
    <button
      class="menu-button glass-button"
      :aria-label="menuOpen ? 'Close menu' : 'Open menu'"
      @click="emit('toggle-menu')"
    >
      <span class="hamburger" :class="{ open: menuOpen }">
        <i></i><i></i><i></i>
      </span>
    </button>

    <button
      class="language-button glass-button"
      aria-label="Switch language"
      @click="emit('toggle-language')"
    >
      <span :class="{ active: language === 'zh' }">中</span>
      <b>/</b>
      <span :class="{ active: language === 'en' }">EN</span>
    </button>

    <Transition name="menu-fade">
      <div v-if="menuOpen" class="menu-overlay">
        <nav class="menu-list" aria-label="Main navigation">
          <button
            v-for="(item, index) in items"
            :key="item.id"
            class="menu-item"
            @click="emit('navigate', item.id)"
          >
            <span class="menu-index">0{{ index + 1 }}</span>
            <span class="menu-primary">
              {{ language === "zh" ? item.zh : item.en }}
            </span>
            <span class="menu-secondary">
              {{ language === "zh" ? item.en : item.zh }}
            </span>
          </button>
        </nav>

        <div class="menu-signature">🐙 Mascott</div>
        <div class="menu-hint">SELECT / ENTER</div>
      </div>
    </Transition>
  </header>
</template>