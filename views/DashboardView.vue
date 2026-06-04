<script setup>
import { ref, onMounted } from 'vue';
import MyNavbar from '../components/MyNavbar.vue';

const greeting = ref("");

onMounted(() => {
  const namaUser = localStorage.getItem("namaUser");
  const hours = new Date().getHours();

  let message =
    hours < 11
      ? "Selamat Pagi"
      : hours < 15
        ? "Selamat Siang"
        : hours < 19
          ? "Selamat Sore"
          : "Selamat Malam";

  greeting.value = `${message}, ${namaUser || "Tamu"}!`;
});
</script>

<template>
  <MyNavbar />

  <div class="greeting-card">
    <h1 class="greeting">{{ greeting }}</h1>
  </div>
</template>

<style scoped>
.greeting-card {
  width: fit-content;
  margin: 35px auto;
  padding: 20px 40px;

  background: linear-gradient(
    135deg,
    #0f4c81 0%,
    #1b6dc1 50%,
    #3d8ae0 100%
  );

  border-radius: 18px;

  box-shadow:
    0 12px 30px rgba(27, 109, 193, 0.25),
    0 5px 15px rgba(0, 0, 0, 0.08);

  transition: all 0.3s ease;
}

.greeting-card:hover {
  transform: translateY(-3px);
}

.greeting {
  margin: 0;
  color: #ffffff;
  font-size: 30px;
  font-weight: 700;
  text-align: center;
}

@media (max-width: 768px) {
  .greeting-card {
    width: 90%;
    padding: 15px;
  }

  .greeting {
    font-size: 24px;
  }
}
</style>