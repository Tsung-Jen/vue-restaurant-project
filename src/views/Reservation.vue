<template>
  <div class="max-w-xl mx-auto px-6 py-16">
    <h1 class="text-3xl font-bold mb-8 text-center">線上訂位</h1>

    <form @submit.prevent="submitForm" class="space-y-6">
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
        class="w-full bg-red-600 text-white py-3 rounded font-semibold hover:bg-red-700 transition"
      >
        送出訂位
      </button>
    </form>
  </div>

  <SuccessModal :visible="showSuccess" @close="showSuccess = false" />
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";
import SuccessModal from "../components/SuccessModal.vue";

const showSuccess = ref(false);

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

function submitForm() {
  if (!validate()) return;

  console.log("Reservation:", { ...form });

  showSuccess.value = true;
}

function inputClass(error?: string) {
  return [
    "input",
    error
      ? "border-red-500 focus:ring-red-500"
      : "border-gray-300 focus:ring-red-400",
  ];
}
</script>
