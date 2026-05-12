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
		{ value: '<8%', desc: 'Rumah tangga di Indonesia yang menyedot lumpur tinja secara berkala.', source: '(UNICEF Indonesia, 2022)' },
		{ value: '2%', desc: 'Penduduk perkotaan memiliki akses saluran pembuangan air limbah (sewerage).', source: '(World Bank, 2020)' },
		{ value: '50%', desc: 'Penduduk Indonesia usia di atas 10 tahun belum mencuci tangan dengan sabun pada waktu-waktu kritis.', source: '(UNICEF Indonesia - WASH Acts, 2022)' }
	])

	const changePage = async (pageName) => {
		currentPage.value = pageName;
		window.scrollTo({ top: 0, behavior: 'smooth' });
		await nextTick();
		setTimeout(() => { AOS.refreshHard(); }, 100);
	}

	onMounted(() => { AOS.init({ duration: 1500, once: true}); })
</script>

<style scoped>
	.fade-enter-active, .fade-leave-active { transition: opacity 0.3s ease; }
	.fade-enter-from, .fade-leave-to { opacity: 0; }
</style>