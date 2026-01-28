<template>
  <header class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">
      <!-- Logo / Restaurant Name -->
      <router-link to="/" class="text-xl font-bold text-red-600">
        老地方中餐廳
      </router-link>

      <!-- Navigation -->
      <nav class="flex items-center space-x-6">
        <router-link
          to="/"
          class="text-gray-700 hover:text-red-600 transition"
          active-class="text-red-600 font-semibold"
        >
          首頁
        </router-link>

        <router-link
          to="/reservation"
          class="bg-red-600 text-white px-4 py-2 rounded-lg hover:bg-red-700 transition"
          active-class="ring-2 ring-red-400"
        >
          線上訂位
        </router-link>
      </nav>
    </div>
  </header>
</template>

<script setup lang="ts"></script>
