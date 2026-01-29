<template>
  <Teleport to="body">
    <div
      v-if="visible"
      class="fixed inset-0 z-50 flex items-center justify-center bg-black/50"
    >
      <div
        class="bg-white rounded-lg shadow-lg max-w-sm w-full p-6 text-center"
      >
        <h2 class="text-2xl font-bold mb-4 text-green-600">訂位成功 🎉</h2>

        <p class="mb-6 text-gray-700">我們已收到您的訂位資訊，期待您的光臨！</p>

        <div class="flex flex-col gap-3">
          <button class="border rounded py-2 hover:bg-gray-100" @click="close">
            繼續修改
          </button>

          <button
            class="bg-red-600 text-white rounded py-2 hover:bg-red-700"
            @click="resetAndClose"
          >
            重新填寫
          </button>

          <button class="text-sm text-gray-500 underline" @click="goHome">
            返回首頁
          </button>
        </div>
      </div>
    </div>
  </Teleport>
</template>

<script setup lang="ts">
import { useRouter } from "vue-router";

defineProps<{
  visible: boolean;
}>();

const emit = defineEmits(["close", "reset"]);
const router = useRouter();

function close() {
  emit("close");
}

function goHome() {
  emit("close");
  router.push("/");
}

function resetAndClose() {
  emit('reset')
  emit('close')
}

</script>
