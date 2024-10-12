<script>
	import Fly from '$lib/Fly.svelte';
	import { goto } from '$app/navigation';

	let hello = [
		{ judul: 'Kaigo/Caregiver', image: 'kaigo.jpg' },
		{ judul: 'Building Cleaning', image: 'building.webp' },
		{ judul: 'Manufacture', image: 'manufacture.png' },
		{ judul: 'Industri Konstruksi', image: 'konstrukti.jpg' },
		{ judul: 'Pembuatan kapal & Mesin Kapal', image: 'kapal.jpg' },
		{ judul: 'Pengolahan Makanan Minuman', image: 'makan.jpg' },
		{ judul: 'Perhotelan', image: 'hotel.webp' },
		{ judul: 'Pertanian', image: 'tani.webp' },
		{ judul: 'Ground Handling', image: 'gh.jpeg' },
		{ judul: 'Perbaikan & Perawatan Mobil', image: 'mobil.jpg' }
	];
</script>

<div class="flex justify-center items-center flex-col mt-10 mb-10">
	<h1 class="text-[#0162AE] font-extrabold text-3xl">Program Cahaya Titian Insantama</h1>
	<h3 class="text-[#0162AE] text-xl">Visa kerja sesuai dengan bidang specific skill workers</h3>

	<div class="flex flex-wrap justify-center items-center gap-10 mt-10">
		{#each hello as g}
			<div class="bg-white p-2 pb-10 w-1/4">
				<div class="h-[200px] overflow-hidden">
					<img class="h-[200px] w-full object-cover" src={g.image} alt="" />
				</div>
				<div class="bg-[#0162AE] w-1/2 mt-4 p-1"></div>
				<h2 class="text-[#0162AE] text-2xl font-semibold">{g.judul}</h2>
			</div>
		{/each}
	</div>
</div>
<Fly />
