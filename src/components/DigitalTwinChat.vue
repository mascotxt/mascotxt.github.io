<script setup lang="ts">
import { nextTick, ref } from "vue";

const messages = ref([
  {
    from: "twin",
    text: "你好。我是 Mascott 的数字孪生版本。你可以随便问我一些关于他的事情。",
  },
]);

const input = ref("");
const busy = ref(false);
const messagesBox = ref<HTMLElement | null>(null);

const presets: Record<string, string> = {
  "你是谁": "我是 Mascott 的数字孪生版本。目前我主要负责展示他的公开信息与兴趣。",
  "他的兴趣是什么": "兴趣比较杂：计算机、AI、数学、脑机接口、认知科学、神经科学，以及游戏、音乐和各种新鲜事物。",
  "他在哪里上学": "他目前就读于天津大学香港理工大学深圳未来技术学院。",
  "他的昵称是什么": "🐙。",
};

async function send() {
  const text = input.value.trim();
  if (!text || busy.value) return;

  messages.value.push({ from: "user", text });
  input.value = "";
  busy.value = true;
  await nextTick();
  messagesBox.value?.scrollTo({ top: messagesBox.value.scrollHeight, behavior: "smooth" });

  window.setTimeout(async () => {
    const answer =
      Object.entries(presets).find(([key]) => text.includes(key))?.[1] ??
      "这个问题目前还没有被写进我的公开资料。你可以换一个问题试试。";

    messages.value.push({ from: "twin", text: answer });
    busy.value = false;
    await nextTick();
    messagesBox.value?.scrollTo({ top: messagesBox.value.scrollHeight, behavior: "smooth" });
  }, 450);
}
</script>

<template>
  <div class="chat-window">
    <div class="chat-topbar">
      <div>
        <span class="status-dot"></span>
        <span>Digital Twin</span>
      </div>
      <span class="chat-model">MASCOTT / LOCAL</span>
    </div>

    <div ref="messagesBox" class="chat-messages">
      <div
        v-for="(message, index) in messages"
        :key="index"
        class="chat-message"
        :class="message.from"
      >
        {{ message.text }}
      </div>

      <div v-if="busy" class="chat-message twin typing">
        <span></span><span></span><span></span>
      </div>
    </div>

    <form class="chat-input-wrap" @submit.prevent="send">
      <input
        v-model="input"
        autocomplete="off"
        placeholder="输入消息……"
        maxlength="300"
      />
      <button type="submit" aria-label="Send">↑</button>
    </form>
  </div>
</template>