<script setup lang="ts">
import { computed, ref } from "vue";

const props = defineProps<{ open: boolean }>();
const emit = defineEmits<{ close: []; submitted: [] }>();

const name = ref("");
const device = ref("");
const otherDevice = ref("");
const content = ref("");
const submitted = ref(false);

const devices = ["iPhone", "Android", "iPad", "Windows", "MacBook", "其他"];

const finalDevice = computed(() =>
  device.value === "其他" ? otherDevice.value.trim() : device.value
);

function submit() {
  if (!name.value.trim() || !finalDevice.value || !content.value.trim()) return;

  submitted.value = true;

  window.setTimeout(() => {
    submitted.value = false;
    name.value = "";
    device.value = "";
    otherDevice.value = "";
    content.value = "";
    emit("submitted");
    emit("close");
  }, 900);
}
</script>

<template>
  <Transition name="modal">
    <div v-if="props.open" class="modal-backdrop" @click.self="emit('close')">
      <section class="feedback-modal" role="dialog" aria-modal="true">
        <button class="modal-close" aria-label="Close" @click="emit('close')">×</button>

        <div v-if="submitted" class="success-state">
          <div class="success-mark">✓</div>
          <h3>感谢反馈。</h3>
          <p>Thank you.</p>
        </div>

        <template v-else>
          <div class="modal-kicker">MASCOTT / FEEDBACK</div>
          <h3>反馈 <span>Feedback</span></h3>

          <label>
            称呼
            <input v-model="name" placeholder="怎么称呼你？" maxlength="40" />
          </label>

          <fieldset>
            <legend>设备</legend>
            <div class="device-grid">
              <label v-for="item in devices" :key="item" class="device-option">
                <input v-model="device" type="radio" name="device" :value="item" />
                <span>{{ item }}</span>
              </label>
            </div>
          </fieldset>

          <label v-if="device === '其他'">
            其他设备
            <input v-model="otherDevice" placeholder="请输入设备名称" maxlength="60" />
          </label>

          <label>
            反馈内容
            <textarea
              v-model="content"
              rows="5"
              placeholder="告诉我你的想法……"
              maxlength="1000"
            />
          </label>

          <button
            class="submit-button"
            :disabled="!name.trim() || !finalDevice || !content.trim()"
            @click="submit"
          >
            提交反馈
            <span>→</span>
          </button>
        </template>
      </section>
    </div>
  </Transition>
</template>