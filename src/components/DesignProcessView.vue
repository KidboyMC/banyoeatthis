<template>
	<div class="min-h-screen bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
		<div class="max-w-7xl mx-auto space-y-12">
			<div class="text-center" data-aos="fade-down">
				<h1 class="text-3xl font-extrabold text-gray-900 sm:text-4xl">Design Process</h1>
				<p class="mt-4 text-lg text-gray-500 max-w-3xl mx-auto">
					Proses perancangan platform Sistem Informasi Pintu Darurat Layanan Sanitasi Lingkungan untuk mendukung SDG 6 (Air Bersih dan Sanitasi Layak).
				</p>
			</div>

			<section class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden" data-aos="fade-up">
				<div class="bg-[#26BDE2] px-6 py-4">
					<h2 class="text-xl font-bold text-white">1. Empathy and Research</h2>
				</div>
				<div class="p-6 md:p-8 space-y-8">
					<div>
						<h3 class="text-lg font-semibold text-gray-900 mb-4 flex items-center">
							<span class="bg-blue-100 text-blue-700 w-8 h-8 rounded-full flex items-center justify-center mr-3">A</span>
							Temuan Survei & Identifikasi Masalah
						</h3>
						<ul class="grid grid-cols-1 md:grid-cols-2 gap-4">
							<li v-for="(item, index) in surveyResults" :key="index" class="flex items-start">
								<svg class="h-6 w-6 text-green-500 mr-2 shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
								</svg>
								<span class="text-gray-600 text-sm leading-relaxed">{{ item }}</span>
							</li>
						</ul>
					</div>

					<div>
						<h3 class="text-lg font-semibold text-gray-900 mb-4 flex items-center">
							<span class="bg-blue-100 text-blue-700 w-8 h-8 rounded-full flex items-center justify-center mr-3">B</span>
							Matriks Riset Solusi Saat Ini
						</h3>
						<div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
							<div v-for="comp in competitors" :key="comp.name" class="border border-gray-200 rounded-lg p-5 hover:shadow-md transition-shadow">
								<h4 class="font-bold text-gray-900 text-lg">{{ comp.name }}</h4>
								<div class="mt-3 space-y-2 text-sm">
									<p><span class="font-semibold text-gray-700">Fokus:</span> {{ comp.focus }}</p>
									<p><span class="font-semibold text-gray-700">Kesenjangan:</span> <span class="text-red-600">{{ comp.gap }}</span></p>
								</div>
							</div>
						</div>
					</div>
				</div>
			</section>

			<section class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden" data-aos="fade-up">
				<div class="bg-[#10B981] px-6 py-4">
					<h2 class="text-xl font-bold text-white">2. Ideation (Mind Map)</h2>
				</div>
				<div class="p-6 md:p-8">
					<p class="text-gray-600 mb-6">Mengkategorikan solusi untuk mengatasi masalah sanitasi air dan BABS di wilayah pemukiman padat perkotaan.</p>
					<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
						<div v-for="idea in ideations" :key="idea.title" class="bg-teal-50 rounded-xl p-5 border border-teal-100">
							<h3 class="font-bold text-teal-800 mb-3 border-b border-teal-200 pb-2">{{ idea.title }}</h3>
							<ul class="space-y-2">
								<li v-for="item in idea.items" :key="item" class="text-sm text-teal-900 flex items-center">
									<span class="w-1.5 h-1.5 bg-teal-500 rounded-full mr-2"></span>
									{{ item }}
								</li>
							</ul>
						</div>
					</div>
				</div>
			</section>

			<section class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden" data-aos="fade-up">
				<div class="bg-[#F59E0B] px-6 py-4">
					<h2 class="text-xl font-bold text-white">3. Prototyping & Solusi Final</h2>
				</div>
				<div class="p-6 md:p-8 space-y-8">
					<div>
						<h3 class="text-lg font-semibold text-gray-900 mb-4 border-b pb-2">Analisis Starburst (4W 1H)</h3>
						<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
							<div v-for="star in starburst" :key="star.q" class="bg-gray-50 p-4 rounded-lg border border-gray-100">
								<span class="text-xs font-extrabold text-indigo-600 uppercase tracking-wider">{{ star.q }}</span>
								<p class="mt-1 text-sm text-gray-700">{{ star.a }}</p>
							</div>
						</div>
					</div>

					<div>
						<h3 class="text-lg font-semibold text-gray-900 mb-4 border-b pb-2">Ekstraksi LEAN Canvas</h3>
						<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
							<div class="bg-red-50 p-5 rounded-xl border border-red-100">
								<h4 class="font-bold text-red-800 mb-2">Problem</h4>
								<p class="text-sm text-red-900">Kurangnya akses informasi vendor sanitasi terpercaya, dan aspirasi warga terkait drainase mampet sering tersumbat lambatnya birokrasi.</p>
							</div>
							<div class="bg-green-50 p-5 rounded-xl border border-green-100">
								<h4 class="font-bold text-green-800 mb-2">Proposed Solution</h4>
								<p class="text-sm text-green-900">Platform web pencarian & pelaporan ringan dengan rekomendasi otomatis berdasarkan analisis masalah dan fitur kontak "sekali klik".</p>
							</div>
							<div class="bg-purple-50 p-5 rounded-xl border border-purple-100">
								<h4 class="font-bold text-purple-800 mb-2">Unique Value Proposition</h4>
								<p class="text-sm text-purple-900">Satu pintu jembatan digital instan antara warga dan penyedia jasa (zero-friction onboarding), didesain ringan untuk low-data mode.</p>
							</div>
						</div>
					</div>
					
				</div>
			</section>

		</div>
	</div>
</template>

<script setup>
import { ref } from 'vue'

const surveyResults = ref([
	'Akses sanitasi dasar (toilet pribadi leher angsa, septic tank) umumnya sudah baik.',
	'Fasilitas toilet di area publik/kampus cukup terawat dan layak.',
	'Sistem drainase publik masih kurang optimal, memicu genangan air saat hujan.',
	'Kurangnya standardisasi toilet publik (minimnya tempat sampah khusus kebersihan).',
	'Masih terdapat warga yang membuang limbah langsung ke selokan karena kurang edukasi.'
])

const competitors = ref([
	{
		name: 'JSDP (Jakarta Sewerage)',
		focus: 'Sistem sanitasi perpipaan, pengolahan air limbah skala besar.',
		gap: 'Belum menjangkau pemukiman informal/pinggiran; cakupan baru ~12%.'
	},
	{
		name: 'Perumda Paljaya',
		focus: 'Layanan sedot tinja dan tangki septik biofilter untuk rumah tangga/kantor.',
		gap: 'Kurang terintegrasi secara digital; pendekatan masih berorientasi teknis.'
	},
	{
		name: 'IPAL SANFAB',
		focus: 'Pengolahan air limbah terkontaminasi untuk komunitas/faskes.',
		gap: 'Kapasitas desain terbatas untuk beban besar & biaya kurang terjangkau.'
	}
])

const ideations = ref([
	{
		title: 'Informasi & Edukasi',
		items: ['Newsletter program sanitasi', 'Definisi & manfaat sanitasi', 'Berita terkini mengenai limbah']
	},
	{
		title: 'Program Kelembagaan',
		items: ['Sanitasi berbasis sekolah/kampus', 'Subsidi pembangunan sanitasi', 'Instalasi toilet standar leher angsa']
	},
	{
		title: 'Aksi Komunitas',
		items: ['Seminar kesadaran lingkungan', 'Gotong royong pembersihan bulanan', 'Pembuatan konten edukasi publik']
	},
	{
		title: 'Pengawasan Daerah',
		items: ['Pengawasan tingkat kelurahan', 'Anggaran khusus pemerintah', 'Imbauan perataan instalasi septic tank']
	}
])

const starburst = ref([
	{ q: 'Who (Siapa)', a: 'Ketua RT/RW, warga area perumahan padat, dan pengelola restoran.' },
	{ q: 'What (Apa)', a: 'Memudahkan akses informasi vendor sanitasi dan menyalurkan aspirasi keluhan drainase.' },
	{ q: 'Why (Mengapa)', a: 'Untuk mencegah banjir, kerusakan properti, dan penyebaran penyakit fecal-oral.' },
	{ q: 'Where (Dimana)', a: 'Wilayah perkotaan dan perumahan padat, diakses secara mobile (smartphone/laptop).' },
	{ q: 'How (Bagaimana)', a: 'User mencari list perusahaan sanitasi atau mengisi form laporan yang diteruskan ke publik/vendor.' }
])
</script>