<template>
	<div class="min-h-screen bg-[#F8F9FA] font-sans text-gray-800">
		<nav class="bg-[#0f1115] text-white px-8 py-4 flex justify-between items-center sticky top-0 z-50">
			<div class="flex items-center gap-3 cursor-pointer" @click="currentPage = 'Home'">
				<img src="./assets/logo.png" class="w-10" alt="Logo">
				<span class="font-semibold text-lg">Banyoe.at.this</span>
			</div>
			
			<div class="hidden md:flex space-x-10 items-center text-sm font-medium">
				<a v-for="link in navLinks" :key="link.name" href="#" 
					@click.prevent="changePage(link.name)"
					:class="[currentPage === link.name ? 'bg-white text-black px-5 py-2 rounded-full' : 'hover:text-gray-300']">
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
	import { ref, computed, nextTick, onMounted } from 'vue'
	import AOS from 'aos'

	import HomeView from './components/HomeView.vue'
	import SwotView from './components/SwotView.vue'
	import DesignProcessView from './components/DesignProcessView.vue'
	import TrelloBoardView from './components/TrelloBoardView.vue'

	const currentPage = ref('Home')

	const pages = {
		'Home': HomeView,
		'Design Process': DesignProcessView,
		'SWOT Analysis': SwotView,
		'Trello Board': TrelloBoardView
	}

	const activeComponent = computed(() => {
		return pages[currentPage.value] || HomeView 
	})

	const navLinks = [{ name: 'Home' }, { name: 'Design Process' }, { name: 'SWOT Analysis' }, { name: 'Trello Board' }]

	const statisticsSdg6 = ref([
		{ value: '25 Juta', desc: 'Masyarakat Indonesia tidak menggunakan toilet.', source: '(UNICEF Indonesia, 2019)' },
		{ value: '89%', desc: 'Sumber air dilaporkan tercemar bakteri feses.', source: '(TheBorgenProject, 2024)' },
		{ value: '1.600', desc: 'Desa melaporkan kelangkaan air bersih.', source: '(UNESA, 2025)' },
		{ value: '2%', desc: 'Penduduk perkotaan memiliki akses saluran pembuangan air limbah (sewerage).', source: '(World Bank, 2020)' },
		{ value: '21 dari 1.000', desc: 'Anak di bawah 5 tahun meninggal akibat kualitas air yang buruk.', source: '(TheBorgenProject, 2024)' }
	])

	const statisticsSdg3 = ref([
		{ value: '9 Juta', desc: 'Kematian dini di seluruh dunia setiap tahunnya diakibatkan oleh polusi udara, air, dan tanah beracun.', source: '(The Lancet Commission on Pollution and Health, 2022)' },
		{ value: '2 Juta', desc: 'Nyawa melayang secara global setiap tahunnya akibat paparan langsung bahan kimia berbahaya.', source: '(World Health Organization, 2021)' },
		{ value: '70%', desc: 'Sumber air minum rumah tangga di Indonesia dilaporkan telah terkontaminasi oleh limbah bakteri feses dan polutan.', source: '(UNICEF & Kemenkes RI, 2022)' },
		{ value: '99%', desc: 'Populasi global saat ini menghirup udara yang melebihi batas aman kualitas udara WHO, penuh dengan polutan penyebab penyakit pernapasan.', source: '(World Health Organization, 2022)' },
		{ value: '1,4 Juta', desc: 'Kasus kematian tahunan yang secara langsung disebabkan oleh konsumsi air yang tercemar dan sanitasi lingkungan yang buruk.', source: '(World Health Organization, 2023)' }
	])

	const changePage = async (pageName) => {
		currentPage.value = pageName;
		window.scrollTo({ top: 0, behavior: 'smooth' });
		await nextTick();
		setTimeout(() => { AOS.refreshHard(); }, 100);
	}

	onMounted(() => { AOS.init({ duration: 1500 }); })
</script>

<style scoped>
	.fade-enter-active, .fade-leave-active { transition: opacity 0.3s ease; }
	.fade-enter-from, .fade-leave-to { opacity: 0; }
</style>