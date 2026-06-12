<template>
  <div class="min-h-screen bg-[#F8F9FA] font-sans text-gray-800">
    <nav
      class="bg-[#0f1115] text-white px-8 py-4 flex justify-between items-center sticky top-0 z-50"
    >
      <div
        class="flex items-center gap-3 cursor-pointer"
        @click="currentPage = 'Home'"
      >
        <img src="./assets/logo.png" class="w-10" alt="Logo" />
        <span class="font-semibold text-lg">Banyoe.at.this</span>
      </div>

      <div class="hidden md:flex space-x-10 items-center text-sm font-medium">
        <a
          v-for="link in navLinks"
          :key="link.name"
          href="#"
          @click.prevent="changePage(link.name)"
          :class="[
            currentPage === link.name
              ? 'bg-white text-black px-5 py-2 rounded-full'
              : 'hover:text-gray-300',
          ]"
        >
          {{ link.name }}
        </a>
      </div>
    </nav>

    <main class="max-w-6xl mx-auto px-6 py-16">
      <transition name="fade" mode="out-in">
        <component
          :is="activeComponent"
          :statistics-sdg6="statisticsSdg6"
          :statistics-sdg3="statisticsSdg3"
        />
      </transition>
    </main>
  </div>
</template>

<script setup>
import { ref, computed, nextTick, onMounted } from "vue";
import AOS from "aos";

import HomeView from "./components/HomeView.vue";
import SwotView from "./components/SwotView.vue";
import DesignProcessView from "./components/DesignProcessView.vue";

const currentPage = ref("Home");

const pages = {
  Home: HomeView,
  "Design Process": DesignProcessView,
  "SWOT Analysis": SwotView,
};

const activeComponent = computed(() => {
  return pages[currentPage.value] || HomeView;
});

const navLinks = [
  { name: "Home" },
  { name: "Design Process" },
  { name: "SWOT Analysis" },
];

const statisticsSdg6 = ref([
  {
    value: "10,21%",
    desc: "Akses layanan sanitasi publik dan institusi yang benar-benar aman di Indonesia pada tahun 2022.",
    source: "(BPS, 2023)",
  },
  {
    value: "> 50%",
    desc: "Satuan pendidikan di Indonesia belum memiliki akses layanan sanitasi dasar yang berfungsi optimal setiap saat.",
    source: "(UNICEF Indonesia, 2021)",
  },
  {
    value: "E. coli",
    desc: "Kontaminasi bakteri pada air tanah Jakarta sangat tinggi, mengancam institusi pendidikan yang mengandalkan air tanah.",
    source: "(Kementerian Kesehatan RI, 2020)",
  },
  {
    value: "Diare & ISPA",
    desc: "Fasilitas umum dan CTPS yang buruk menjadi penyebab utama penyebaran penyakit infeksi pada kelompok usia produktif.",
    source: "(Kementerian Kesehatan RI, 2021)",
  },
  {
    value: "Produktivitas",
    desc: "Praktik sanitasi kampus yang buruk berkontribusi langsung pada hilangnya hari belajar efektif mahasiswa akibat penyakit.",
    source: "(UNICEF Indonesia, 2019)",
  },
]);

const changePage = async (pageName) => {
  currentPage.value = pageName;
  window.scrollTo({ top: 0, behavior: "smooth" });
  await nextTick();
  setTimeout(() => {
    AOS.refreshHard();
  }, 100);
};

onMounted(() => {
  AOS.init({ duration: 1500, once: true });
});
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
