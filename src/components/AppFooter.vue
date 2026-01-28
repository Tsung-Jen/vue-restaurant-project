<template>
  <footer class="bg-gray-900 text-gray-200 mt-20">
    <div class="max-w-6xl mx-auto px-6 py-12 grid gap-8 md:grid-cols-3">
      <!-- Restaurant Info -->
      <div>
        <h3 class="text-lg font-semibold mb-4 text-white">老地方中餐廳</h3>
        <p class="text-sm leading-relaxed text-gray-400">
          提供正宗家常中菜，適合家庭聚餐與朋友聚會。
        </p>
      </div>

      <!-- Address -->
      <div>
        <h4 class="font-semibold mb-3 text-white">地址</h4>
        <p class="text-sm text-gray-400">
          Musterstraße 12<br />
          12345 Berlin<br />
          Germany
        </p>
      </div>

      <!-- Opening Hours -->
      <div>
        <h4 class="font-semibold mb-3 text-white">營業時間</h4>
        <ul class="text-sm text-gray-400 space-y-1">
          <li>週一 – 週五：11:30 – 22:00</li>
          <li>週六：11:30 – 23:00</li>
          <li>週日：休息</li>
        </ul>
      </div>
    </div>

    <!-- Bottom -->
    <div
      class="border-t border-gray-800 text-center py-4 text-sm text-gray-500"
    >
      © {{ year }} 老地方中餐廳 · All rights reserved.
    </div>
  </footer>
</template>

<script setup lang="ts">
const year = new Date().getFullYear();
</script>
