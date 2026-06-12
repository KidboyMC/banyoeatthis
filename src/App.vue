<template>
  <div class="min-h-screen bg-[#F8F9FA] font-sans text-gray-800">
    <nav
      class="bg-[#0f1115] text-white px-6 md:px-8 py-4 sticky top-0 z-50 transition-all duration-300"
    >
      <div class="flex justify-between items-center w-full">
        <div
          class="flex items-center gap-3 cursor-pointer"
          @click="changePage('Home')"
        >
          <img src="./assets/logo.png" class="w-8 md:w-10" alt="Logo" />
          <span class="font-semibold text-base md:text-lg">Banyoe.at.this</span>
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

        <button
          @click="isMobileMenuOpen = !isMobileMenuOpen"
          class="md:hidden flex items-center p-2 focus:outline-none"
        >
          <svg
            v-if="!isMobileMenuOpen"
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            ></path>
          </svg>
          <svg
            v-else
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            ></path>
          </svg>
        </button>
      </div>

      <transition name="slide-down">
        <div
          v-if="isMobileMenuOpen"
          class="md:hidden pt-6 pb-4 border-t border-gray-800 mt-4"
        >
          <div class="flex flex-col space-y-2">
            <a
              v-for="link in navLinks"
              :key="link.name"
              href="#"
              @click.prevent="changePage(link.name)"
              :class="[
                currentPage === link.name
                  ? 'bg-white text-black font-semibold'
                  : 'text-gray-300 hover:bg-gray-800',
                'px-4 py-3 rounded-xl text-sm transition-colors',
              ]"
            >
              {{ link.name }}
            </a>
          </div>
        </div>
      </transition>
    </nav>

    <main
      class="max-w-6xl mx-auto px-4 md:px-6 py-12 md:py-16 overflow-x-hidden"
    >
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
const isMobileMenuOpen = ref(false);

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
  isMobileMenuOpen.value = false;
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

.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease-in-out;
  transform-origin: top;
}
.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
