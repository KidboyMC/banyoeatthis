<template>
  <div class="min-h-screen bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto space-y-12">
      <div class="text-center" data-aos="fade-down">
        <h1 class="text-3xl font-extrabold text-gray-900 sm:text-4xl">
          Design Process
        </h1>
        <p class="mt-4 text-lg text-gray-500 max-w-3xl mx-auto">
          Proses perancangan platform Sistem Informasi Pelaporan Sanitasi Kampus
          (UniFlow) untuk mendukung SDG 6.2 di Universitas Negeri Jakarta.
        </p>
      </div>

      <section
        class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden"
        data-aos="fade-up"
      >
        <div class="bg-[#26BDE2] px-6 py-4">
          <h2 class="text-xl font-bold text-white">1. Empathy and Research</h2>
        </div>
        <div class="p-6 md:p-8 space-y-8">
          <div>
            <h3
              class="text-lg font-semibold text-gray-900 mb-4 flex items-center"
            >
              <span
                class="bg-blue-100 text-blue-700 w-8 h-8 rounded-full flex items-center justify-center mr-3"
                >A</span
              >
              Temuan Kondisi Lapangan & Masalah
            </h3>
            <ul class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <li
                v-for="(item, index) in surveyResults"
                :key="index"
                class="flex items-start"
              >
                <svg
                  class="h-6 w-6 text-green-500 mr-2 shrink-0"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                  />
                </svg>
                <span class="text-gray-600 text-sm leading-relaxed">{{
                  item
                }}</span>
              </li>
            </ul>
          </div>

          <div>
            <h3
              class="text-lg font-semibold text-gray-900 mb-4 flex items-center"
            >
              <span
                class="bg-blue-100 text-blue-700 w-8 h-8 rounded-full flex items-center justify-center mr-3"
                >B</span
              >
              Matriks Riset Solusi Saat Ini
            </h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div
                v-for="comp in competitors"
                :key="comp.name"
                class="border border-gray-200 rounded-lg p-5 hover:shadow-md transition-shadow"
              >
                <h4 class="font-bold text-gray-900 text-lg">{{ comp.name }}</h4>
                <div class="mt-3 space-y-2 text-sm">
                  <p>
                    <span class="font-semibold text-gray-700">Fokus:</span>
                    {{ comp.focus }}
                  </p>
                  <p>
                    <span class="font-semibold text-gray-700"
                      >Kesenjangan: </span
                    >
                    <span class="text-red-600">{{ comp.gap }}</span>
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section
        class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden"
        data-aos="fade-up"
      >
        <div class="bg-[#10B981] px-6 py-4">
          <h2 class="text-xl font-bold text-white">2. Ideation (Mind Map)</h2>
        </div>
        <div class="p-6 md:p-8">
          <p class="text-gray-600 mb-6">
            Pemetaan struktur masalah dan solusi tata kelola pelaporan sanitasi
            kampus terpusat (UniFlow).
          </p>
          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
            <div
              v-for="idea in ideations"
              :key="idea.title"
              class="bg-teal-50 rounded-xl p-5 border border-teal-100"
            >
              <h3
                class="font-bold text-teal-800 mb-3 border-b border-teal-200 pb-2"
              >
                {{ idea.title }}
              </h3>
              <ul class="space-y-2">
                <li
                  v-for="item in idea.items"
                  :key="item"
                  class="text-sm text-teal-900 flex items-center"
                >
                  <span
                    class="w-1.5 h-1.5 bg-teal-500 rounded-full mr-2 shrink-0"
                  ></span>
                  <span class="leading-tight">{{ item }}</span>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </section>

      <section
        class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden"
        data-aos="fade-up"
      >
        <div class="bg-[#F59E0B] px-6 py-4">
          <h2 class="text-xl font-bold text-white">
            3. Prototyping & Solusi Final
          </h2>
        </div>
        <div class="p-6 md:p-8 space-y-8">
          <div>
            <h3 class="text-lg font-semibold text-gray-900 mb-4 border-b pb-2">
              Analisis Starburst (4W 1H)
            </h3>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
              <div
                v-for="star in starburst"
                :key="star.q"
                class="bg-gray-50 p-4 rounded-lg border border-gray-100"
              >
                <span
                  class="text-xs font-extrabold text-indigo-600 uppercase tracking-wider"
                  >{{ star.q }}</span
                >
                <p class="mt-1 text-sm text-gray-700">{{ star.a }}</p>
              </div>
            </div>
          </div>

          <div>
            <h3 class="text-lg font-semibold text-gray-900 mb-4 border-b pb-2">
              Ekstraksi LEAN Canvas
            </h3>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div class="bg-red-50 p-5 rounded-xl border border-red-100">
                <h4 class="font-bold text-red-800 mb-2">Problem</h4>
                <p class="text-sm text-red-900">
                  Birokrasi pelaporan kerusakan fasilitas yang berjenjang dan
                  lambat. Tidak ada tracking laporan, sehingga kerusakan
                  mengganggu kenyamanan belajar.
                </p>
              </div>
              <div class="bg-green-50 p-5 rounded-xl border border-green-100">
                <h4 class="font-bold text-green-800 mb-2">Proposed Solution</h4>
                <p class="text-sm text-green-900">
                  Platform web pelaporan tanpa login yang presisi dengan
                  direktori mitra. Laporan form langsung dikirim secara
                  real-time ke email Sarpras/teknisi kampus.
                </p>
              </div>
              <div class="bg-purple-50 p-5 rounded-xl border border-purple-100">
                <h4 class="font-bold text-purple-800 mb-2">
                  Unique Value Proposition
                </h4>
                <p class="text-sm text-purple-900">
                  Jalur Cepat Sanitasi Kampus memangkas birokrasi berhari-hari
                  menjadi hitungan menit. Memiliki pemetaan lokasi spesifik
                  (nama fakultas & lantai).
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const surveyResults = ref([
  "Akses sanitasi dasar rumah tangga sudah baik, namun fasilitas di area publik/kampus kerap bermasalah.",
  "Sistem pelaporan kerusakan sarana kampus saat ini dinilai berbelit dan tidak memiliki tracking yang jelas.",
  "Sistem drainase publik kampus masih sering kurang optimal, memicu genangan air saat hujan.",
  "Kurangnya standardisasi dan perawatan rutin pada fasilitas toilet publik fakultas (misal: kran bocor, sabun habis).",
  "Masih diperlukan wadah yang praktis dan menjangkau teknisi/vendor secara langsung.",
]);

const competitors = ref([
  {
    name: "Grup WhatsApp / Organisasi Mahasiswa",
    focus:
      "Wadah penampungan keluhan atau aspirasi mahasiswa yang dikumpulkan pengurus BEM.",
    gap: "Sangat lambat karena birokrasi berjenjang (dari mahasiswa > BEM > Dekanat > Teknisi) dan tidak ada tracking laporan.",
  },
  {
    name: "Lisan ke Petugas Kebersihan",
    focus:
      "Pelaporan langsung secara tatap muka untuk kerusakan di lokasi kejadian.",
    gap: "Petugas lapangan sering tak punya alat teknis besar. Rentan terlupa karena tanpa dokumentasi/form resmi.",
  },
]);

const ideations = ref([
  {
    title: "Pengguna Utama",
    items: [
      "Mahasiswa (Individu/BEM)",
      "Unit Sarana Prasarana (Sarpras)",
      "Petugas Kebersihan / Vendor",
      "Dosen & Tenaga Kependidikan",
    ],
  },
  {
    title: "Jenis Kendala",
    items: [
      "Fasilitas Toilet (Mampet, bau)",
      "Air Bersih (Kran bocor, air mati)",
      "Drainase (Genangan air di fakultas)",
      "Alat Kebersihan (Sabun habis)",
    ],
  },
  {
    title: "Solusi Platform (UniFlow)",
    items: [
      "Akses Web Ringan (tanpa login)",
      "Pemetaan Lokasi Gedung/Lantai",
      "Integrasi Email Notifikasi Otomatis",
      "Direktori Perusahaan Sanitasi",
    ],
  },
  {
    title: "Tujuan & Dampak",
    items: [
      "Mewujudkan visi Green Campus",
      "Memotong birokrasi pelaporan",
      "Mencegah penyakit tular air",
      "Meningkatkan kenyamanan belajar",
    ],
  },
]);

const starburst = ref([
  {
    q: "Who (Siapa)",
    a: "Civitas Akademika UNJ (Mahasiswa, Dosen, Staf), Unit Sarpras, dan Petugas Kebersihan.",
  },
  {
    q: "What (Apa)",
    a: "Memecahkan masalah birokrasi pelaporan perbaikan fasilitas sanitasi yang lambat dan tidak efisien.",
  },
  {
    q: "Why (Mengapa)",
    a: "Mencegah penyakit, menjaga produktivitas belajar, serta mewujudkan standar kebersihan Green Campus UNJ.",
  },
  {
    q: "Where (Dimana)",
    a: "Diaplikasikan pada lingkungan kampus Universitas Negeri Jakarta (area fakultas, perpustakaan, kantin).",
  },
  {
    q: "How (Bagaimana)",
    a: "Pengguna mengisi form web singkat; laporan masuk real-time ke email teknisi. Terdapat pula Direktori vendor untuk pengelola.",
  },
]);
</script>
