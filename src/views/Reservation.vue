<template>
  <div class="max-w-xl mx-auto px-6 py-16">
    <h1 class="text-3xl font-bold mb-8 text-center">線上訂位</h1>

    <form
      @submit.prevent="submitForm"
      :class="{ 'pointer-events-none opacity-70': isSubmitting }"
      class="space-y-6"
    >
      <!-- Name -->
      <div>
        <label class="block mb-1 font-medium">姓名</label>
        <input
          v-model="form.name"
          type="text"
          placeholder="請輸入您的姓名"
          :class="inputClass(errors.name)"
        />
        <p v-if="errors.name" class="error-text">{{ errors.name }}</p>
      </div>

      <!-- Phone -->
      <div>
        <label class="block mb-1 font-medium">電話</label>
        <input
          v-model="form.phone"
          type="tel"
          placeholder="例如：0176 12345678"
          :class="inputClass(errors.phone)"
        />
        <p v-if="errors.phone" class="error-text">{{ errors.phone }}</p>
      </div>

      <!-- Date -->
      <div>
        <label class="block mb-1 font-medium">日期</label>
        <input
          v-model="form.date"
          type="date"
          :class="inputClass(errors.date)"
        />
        <p v-if="errors.date" class="error-text">{{ errors.date }}</p>
      </div>

      <!-- Time -->
      <div>
        <label class="block mb-1 font-medium">時間</label>
        <select v-model="form.time" :class="inputClass(errors.time)">
          <option value="">請選擇時間</option>
          <option v-for="time in timeSlots" :key="time" :value="time">
            {{ time }}
          </option>
        </select>
        <p v-if="errors.time" class="error-text">{{ errors.time }}</p>
      </div>

      <!-- Guests -->
      <div>
        <label class="block mb-1 font-medium">人數</label>
        <input
          v-model.number="form.guests"
          type="number"
          min="1"
          max="20"
          :class="inputClass(errors.guests)"
        />
        <p v-if="errors.guests" class="error-text">{{ errors.guests }}</p>
      </div>

      <!-- Note -->
      <div>
        <label class="block mb-1 font-medium">備註（選填）</label>
        <textarea v-model="form.note" rows="3" class="input" />
      </div>

      <button
        type="submit"
        :disabled="isSubmitting"
        class="w-full py-3 rounded font-semibold transition bg-red-600 text-white disabled:bg-gray-400 disabled:cursor-not-allowed"
      >
        <span v-if="!isSubmitting">送出訂位</span>

        <span v-else class="flex items-center justify-center gap-2">
          <svg
            class="animate-spin h-5 w-5 text-white"
            viewBox="0 0 24 24"
            fill="none"
          >
            <circle
              class="opacity-25"
              cx="12"
              cy="12"
              r="10"
              stroke="currentColor"
              stroke-width="4"
            />
            <path
              class="opacity-75"
              fill="currentColor"
              d="M4 12a8 8 0 018-8v4a4 4 0 00-4 4H4z"
            />
          </svg>
          送出中...
        </span>
      </button>
    </form>
  </div>

  <SuccessModal
    :visible="showSuccess"
    @close="showSuccess = false"
    @reset="resetForm"
  />
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";
import SuccessModal from "../components/SuccessModal.vue";

const showSuccess = ref(false);
const isSubmitting = ref(false);

const form = reactive({
  name: "",
  phone: "",
  date: "",
  time: "",
  guests: 1,
  note: "",
});

const errors = reactive<Record<string, string>>({});

const timeSlots = [
  "11:30",
  "12:00",
  "12:30",
  "13:00",
  "17:30",
  "18:00",
  "18:30",
  "19:00",
  "19:30",
  "20:00",
];

function validate() {
  Object.keys(errors).forEach((key) => delete errors[key]);

  if (!form.name.trim()) {
    errors.name = "請輸入姓名";
  }

  if (!form.phone.trim()) {
    errors.phone = "請輸入電話";
  } else if (!/^[0-9 +()-]{6,20}$/.test(form.phone)) {
    errors.phone = "電話格式不正確";
  }

  if (!form.date) {
    errors.date = "請選擇日期";
  }

  if (!form.time) {
    errors.time = "請選擇時間";
  }

  if (!form.guests || form.guests < 1) {
    errors.guests = "人數至少為 1 人";
  }

  return Object.keys(errors).length === 0;
}

async function submitForm() {
  if (isSubmitting.value) return;
  if (!validate()) return;

  isSubmitting.value = true;

  try {
    // 模擬 API 呼叫
    await new Promise((resolve) => setTimeout(resolve, 1500));

    console.log("Reservation:", { ...form });

    showSuccess.value = true;
  } catch (error) {
    console.error(error);
    alert("送出失敗，請稍後再試");
  } finally {
    isSubmitting.value = false;
  }
}

function inputClass(error?: string) {
  return [
    "input",
    error
      ? "border-red-500 focus:ring-red-500"
      : "border-gray-300 focus:ring-red-400",
  ];
}

function resetForm() {
  form.name = "";
  form.phone = "";
  form.date = "";
  form.time = "";
  form.guests = 1;
  form.note = "";

  Object.keys(errors).forEach((key) => delete errors[key]);
}
</script>
