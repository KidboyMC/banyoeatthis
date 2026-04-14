<template>
	<div class="min-h-screen bg-[#F8F9FA] font-sans text-gray-800 selection:bg-[#26BDE2] selection:text-white">
		<nav class="bg-[#0f1115] text-white px-8 py-4 flex justify-between items-center">
			<div class="flex items-center gap-3">
				<div class="w-10 h-10 border-2 border-[#26BDE2] rounded-full flex items-center justify-center p-1">
					<img src="./assets/logo.png" alt="Website Logo">
				</div>
				<span class="font-semibold text-lg tracking-wide">Banyoe.at.this</span>
			</div>
			
			<div class="hidden md:flex space-x-10 items-center text-sm font-medium">
				<a 
					v-for="(link, index) in navLinks" 
					:key="index" 
					href="#" 
					:class="[
						'transition-colors duration-200 cursor-pointer',
						link.active ? 'bg-white text-black px-5 py-2 rounded-full' : 'hover:text-gray-300'
					]"
				>
					{{ link.name }}
				</a>
			</div>
		</nav>

		<main class="max-w-6xl mx-auto px-6 py-16">
			<section class="mb-32" data-aos="fade-right">
				<h1 class="text-4xl md:text-5xl font-bold text-[#333333] mb-10">Sustainable<br>Development Goals</h1>
				<div class="grid md:grid-cols-2 gap-12 items-start">
					<img 
						src="./assets/sdgs.png" 
						alt="17 Sustainable Development Goals Grid" 
						class="w-full rounded-md shadow-sm" 
					/>
					<div>
						<span class="inline-block bg-[#333333] text-white px-5 py-2 rounded-full text-sm font-medium mb-6">
							About SDGs
						</span>
						<p class="text-gray-700 text-sm leading-relaxed mb-8 text-justify">
							Sustainable Development Goals (SDGs) atau Tujuan Pembangunan Berkelanjutan adalah serangkaian 17 tujuan yang dicanangkan oleh Perserikatan Bangsa-Bangsa (PBB) sebagai cetak biru untuk mencapai masa depan yang lebih baik dan lebih berkelanjutan bagi semua orang. SDGs diadopsi pada tahun 2015 sebagai bagian dari Agenda 2030 untuk Pembangunan Berkelanjutan. SDGs dirancang untuk mengatasi berbagai tantangan global, termasuk kemiskinan, ketidaksetaraan, perubahan iklim, degradasi lingkungan, perdamaian, dan keadilan.
						</p>
						<div class="flex gap-16">
							<div>
								<h3 class="text-3xl font-bold text-[#333333]">2015</h3>
								<p class="text-sm text-gray-600 mt-1">Founded</p>
							</div>
							<div>
								<h3 class="text-3xl font-bold text-[#333333]">17</h3>
								<p class="text-sm text-gray-600 mt-1">Goals</p>
							</div>
						</div>
					</div>
				</div>
			</section>

			<section class="mb-32" data-aos="fade-left">
				<div class="grid md:grid-cols-2 gap-12 items-center">
					<div>
						<div class="flex items-center gap-6 mb-6">
							<div class="w-20 h-20 bg-[#26BDE2] rounded-xl flex items-center justify-center p-2 shadow-sm shrink-0">
								 <img src="./assets/sdg06.png" alt="SDG 6 Icon" class="w-full h-full object-contain" />
							</div>
							<h2 class="text-4xl md:text-[2.75rem] font-bold text-[#333333] leading-tight">
								SDG 6: Clean<br>Water and<br>Sanitation
							</h2>
						</div>
						<span class="inline-block bg-[#333333] text-white px-5 py-2.5 rounded-full text-xs font-medium">
							Bagian dari United Nations Sustainable Development Goals
						</span>
					</div>
					<div class="h-100 rounded-3xl overflow-hidden shadow-sm">
						<img 
							src="./assets/water.png" 
							alt="Water bubbles" 
							class="w-full h-full object-cover" 
						/>
					</div>
				</div>
			</section>

			<section class="mb-24 text-center flex flex-col items-center" data-aos="fade-up">
				<h2 class="text-3xl md:text-4xl font-bold text-[#333333] mb-8">What is SDG 6?</h2>
				<div class="bg-white/80 backdrop-blur-sm px-8 py-6 rounded-2xl shadow-sm max-w-3xl border border-gray-100">
					<p class="text-gray-700 text-sm leading-relaxed">
						SDG 6 bertujuan memastikan ketersediaan dan pengelolaan air bersih serta sanitasi yang berkelanjutan untuk semua. Akses terhadap air bersih merupakan kebutuhan dasar manusia yang berdampak langsung pada kesehatan, ekonomi, dan kualitas hidup.
					</p>
				</div>
			</section>

			<section class="mb-32 text-center" data-aos="fade-up">
				<h2 class="text-3xl md:text-4xl font-bold text-[#333333] mb-10">Targets of SDG 6</h2>
				<div class="flex flex-wrap justify-center gap-4 max-w-3xl mx-auto">
					<span class="bg-[#333333] text-white px-8 py-3 rounded-full text-sm font-medium shadow-sm">Akses air minum aman</span>
					<span class="bg-[#333333] text-white px-8 py-3 rounded-full text-sm font-medium shadow-sm">Pengurangan pencemaran</span>
					<span class="bg-[#333333] text-white px-8 py-3 rounded-full text-sm font-medium shadow-sm">Sanitasi dan kebersihan</span>
					<span class="bg-[#333333] text-white px-8 py-3 rounded-full text-sm font-medium shadow-sm">Pengelolaan air berkelanjutan</span>
				</div>
			</section>

			<section class="mb-32 flex flex-col items-center" data-aos="fade-left">
				<h2 class="text-4xl md:text-[2.75rem] font-bold text-[#333333] leading-tight text-center mb-6">
					Website Goal: Improve National<br>Water Quality
				</h2>
				<span class="inline-block bg-[#333333] text-white px-6 py-2 rounded-full text-sm font-medium mb-12">
					Selected SDG
				</span>

				<div class="grid md:grid-cols-2 gap-8 items-stretch w-full">
					<div class="bg-white p-8 md:p-10 rounded-3xl shadow-sm border border-gray-50 flex flex-col justify-center">
						<p class="text-gray-700 text-sm leading-relaxed mb-6 text-justify">
							Air bersih dan sanitasi layak adalah isu penting yang ada bagi seluruh dunia. Hal ini disebabkan karena air bersih dan sanitasi layak merupakan komponen atau kebutuhan dasar bagi manusia. Sayangnya, kondisi kebersihan ini masih belum terealisasikan sepenuhnya sehingga hal ini menyebabkan banyak masalah kesehatan pada masyarakat. Website ini dibuat untuk membahas dan memberikan solusi untuk permasalahan ketersediaan air bersih dan sanitasi yang layak di seluruh dunia.
						</p>
						<p class="text-gray-700 text-sm leading-relaxed text-justify">
							Kami berfokus pada Target 6.3 untuk meningkatkan kualitas air nasional dengan menekan polusi dan meminimalkan pembuangan zat kimia berbahaya. Melalui platform ini, kami menyediakan strategi edukatif untuk mendorong peningkatan daur ulang dan penggunaan kembali air secara aman, guna memastikan setiap lapisan masyarakat memiliki akses terhadap sumber air yang bersih dan bebas kontaminasi pada tahun 2030.
						</p>
					</div>
					
					<div class="rounded-3xl overflow-hidden shadow-sm h-full min-h-75">
						<img 
							src="./assets/handWash.png" 
							alt="Hands holding a water drop resembling the Earth" 
							class="w-full h-full object-cover" 
						/>
					</div>
				</div>
			</section>

			<section class="py-10 text-center" data-aos="zoom-in">
				<h2 class="text-4xl font-bold text-[#333333] mb-16">Why It Matters?</h2>
				
				<div class="grid grid-cols-1 md:grid-cols-5 gap-6">
					<div 
						v-for="(stat, index) in statistics" 
						:key="index" 
						class="flex flex-col items-center px-2"
					>
						<div class="bg-[#333333] text-white px-6 py-2.5 rounded-full font-medium text-sm mb-6 whitespace-nowrap">
							{{ stat.value }}
						</div>
						<p class="text-xs text-gray-700 mb-4 h-16 leading-relaxed">
							{{ stat.desc }}
						</p>
						<p class="text-[11px] text-gray-500 font-medium">
							{{ stat.source }}
						</p>
					</div>
				</div>
			</section>

		</main>
	</div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import AOS from 'aos'

// Data Navigasi
const navLinks = ref([
	{ name: 'Home', active: true },
	{ name: 'Design Process ▼', active: false },
	{ name: 'SWOT Analysis', active: false },
	{ name: 'Trello Board', active: false }
])

// Data Statistik
const statistics = ref([
	{ 
		value: '25 Juta', 
		desc: 'Masyarakat Indonesia tidak menggunakan toilet.', 
		source: '(UNICEF Indonesia, 2019)' 
	},
	{ 
		value: '89%', 
		desc: 'Sumber air dilaporkan tercemar bakteri feses.', 
		source: '(TheBorgenProject, 2024)' 
	},
	{ 
		value: '1.600', 
		desc: 'Desa melaporkan kelangkaan air bersih.', 
		source: '(UNESA, 2025)' 
	},
	{ 
		value: '2%', 
		desc: 'Penduduk perkotaan memiliki akses saluran pembuangan air limbah (sewerage).', 
		source: '(World Bank, 2020)' 
	},
	{ 
		value: '21 dari 1.000', 
		desc: 'Anak di bawah 5 tahun meninggal akibat kualitas air yang buruk.', 
		source: '(TheBorgenProject, 2024)' 
	}
])

onMounted(() => {
  AOS.init({
    duration: 1500,
  })
})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

.font-sans {
	font-family: 'Inter', sans-serif;
}
</style>