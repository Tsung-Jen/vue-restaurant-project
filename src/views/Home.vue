<template>
  <div class="min-h-screen bg-gray-50 text-gray-800">
    <!-- Hero Section -->
    <section class="bg-red-600 text-white">
      <div class="max-w-6xl mx-auto px-6 py-20 text-center">
        <h1 class="text-4xl md:text-5xl font-bold mb-6">老地方中餐廳</h1>
        <p class="text-lg md:text-xl mb-8">
          正宗家常中菜，適合家庭聚餐與朋友相聚
        </p>

        <router-link
          to="/reservation"
          class="inline-block bg-white text-red-600 font-semibold px-8 py-3 rounded-lg shadow hover:bg-gray-100 transition"
        >
          線上訂位
        </router-link>
      </div>
    </section>

    <!-- About Section -->
    <section class="py-16">
      <div
        class="max-w-5xl mx-auto px-6 grid md:grid-cols-2 gap-10 items-center"
      >
        <div>
          <h2 class="text-2xl font-bold mb-4">關於我們</h2>
          <p class="leading-relaxed text-gray-600">
            我們提供道地的中式料理，堅持每日新鮮備料，
            無論是家庭聚餐、朋友聚會或商務用餐，
            都希望帶給您溫暖又安心的用餐體驗。
          </p>
        </div>

        <div class="bg-white rounded-xl shadow p-6">
          <ul class="space-y-4">
            <li class="flex justify-between">
              <span class="font-medium">營業時間</span>
              <span>11:30 – 22:00</span>
            </li>
            <li class="flex justify-between">
              <span class="font-medium">電話</span>
              <span>+49 123 456789</span>
            </li>
            <li class="flex justify-between">
              <span class="font-medium">地址</span>
              <span>Berlin Musterstraße 12</span>
            </li>
          </ul>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="bg-gray-100 py-14">
      <div class="text-center">
        <h2 class="text-2xl font-bold mb-4">想要預約座位嗎？</h2>
        <p class="text-gray-600 mb-6">
          線上訂位快速又方便，立即保留您的用餐時段
        </p>

        <router-link
          to="/reservation"
          class="bg-red-600 text-white px-10 py-3 rounded-lg font-semibold hover:bg-red-700 transition"
        >
          前往訂位頁
        </router-link>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
// 首頁暫時不需要邏輯
</script>
