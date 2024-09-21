<script>
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';

	// Array of image URLs
	let images = [
		{
			url: 'gambar4.png',
			desc: '',
			judulSatu: 'Provide Opportunities',
			juduDua: 'For Indonesian youth to become independent individuals'
		},
		{
			url: 'gambar2.png',
			desc: '',
			judulSatu: 'Training and gaining knowledge in Japan.',
			juduDua: 'Impart Japanese work culture, traditions, and professional ethics'
		},
		{
			url: 'gambar3.png',
			desc: '',
			judulSatu: 'Acquire various skills and knowledge from Japan',
			juduDua: 'For a better future in Indonesia.'
		},
		{
			url: 'gambar1.png',
			desc: '',
			judulSatu: 'Contribute to economic growth',
			juduDua: 'Improving the living standards of the people in Indonesia'
		}
	];

	let currentIndex = 0;
	let interval = 5500;

	function nextImage() {
		currentIndex = (currentIndex + 1) % images.length;
	}

	onMount(() => {
		const intervalId = setInterval(nextImage, interval);
		return () => clearInterval(intervalId);
	});
</script>

<div class="relative w-full md:h-[500px] overflow-hidden">
	{#each images as image, i}
		{#if i === currentIndex}
			<div class="overflow-y-hidden min-h-[200px] lg:h-[500px] md:w-5/6 m-auto rounded-sm">
				<img
					src={image.url}
					alt="Slideshow image"
					class=" w-full h-full object-cover"
					in:fade={{ duration: 2000 }}
				/>
				<div
					in:fade={{ duration: 2000 }}
					class="absolute hidden md:block bottom-44 left-48 bg-blue-200 bg-opacity-70 text-white py-10 px-16"
				>
					<h2 class="text-3xl font-extrabold">{image.judulSatu}</h2>
					<p class="font-bold mt-10">{image.desc}</p>
				</div>
				<div
					in:fade={{ duration: 2000 }}
					class="absolute w-1/2 top-0 md:top-auto md:bottom-0 md:left-[500px] bg-orange-400 bg-opacity-30 md:bg-opacity-90 text-white p-2 md:py-10 md:px-16 max-w-[800px]"
				>
					<h2 class="md:text-3xl font-extrabold">{image.juduDua}</h2>
					<p class="font-bold mt-10">{image.desc}</p>
				</div>
			</div>
		{/if}
	{/each}
</div>
