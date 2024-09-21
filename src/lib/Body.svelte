<script>
	import { slide } from 'svelte/transition';
	import { onMount } from 'svelte';

	let divElement; // reference to the div
	let isInView = false;

	onMount(() => {
		const observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					isInView = true;
					console.log('Div is in view!');
				} else {
					isInView = false;
					console.log('Div is out of view!');
				}
			});
		});

		observer.observe(divElement); // start observing the div

		return () => {
			observer.disconnect(); // cleanup when the component is destroyed
		};
	});
</script>

<div class="target min-h-screen" bind:this={divElement}>
	{#if isInView}
		<div
			id="slide-target"
			transition:slide={{ duration: 500 }}
			class="flex flex-col md:flex-row justify-around items-center gap-10 mt-10 lg:mt-10 md:w-5/6 m-auto"
		>
			<div class=" h-[320px] w-[320px] md:h-[600px] md:w-[600px] overflow-hidden">
				<img class="md:h-[600px] rounded-sm" src="Frame1.png" alt="" />
			</div>
			<div class="w-3/4 md:w-1/2 flex flex-col gap-5">
				<div>
					<h2 class="font-extrabold text-[#0162AE] text-lg">Language training</h2>
					<p class="text-[#0162AE]">
						Japanese Language: Through training in hiragana, katakana, kanji, 1300 vocabulary words
						over five (5) months, and the use of Japanese in daily life, we expect our students to
						be able to adapt well to the work environment in Japan.
					</p>
				</div>
				<div>
					<h2 class="font-extrabold text-[#0162AE] text-lg">
						Certified Theoretical and Practical Training:
					</h2>
					<p class="text-[#0162AE]">
						In the fields of airport services, agriculture, hospitality, construction, fisheries,
						and elderly care in Japan.
					</p>
				</div>
				<div>
					<h2 class="font-extrabold text-[#0162AE] text-lg">
						Character Development and Japanese Work Ethos:
					</h2>
					<p class="text-[#0162AE]">Required in every company in Japan.</p>
				</div>
				<div>
					<h2 class="font-extrabold text-[#0162AE] text-lg">High dicipline training program</h2>
					<p class="text-[#0162AE]">
						Instructions on the values of honesty, loyalty, and obedience to the company, which are
						crucial for personal development. Regular physical exercise to ensure students are
						healthy, strong, reliable, and resilient
					</p>
				</div>
			</div>
		</div>
	{/if}

	<div class="flex justify-center flex-col items-center mt-56">
		<h2 class="text-3xl text-orange-400 font-extrabold">Cabang Kami</h2>
		<img class="mt-10 mb-96 w-2/3" src="gambar10.png" alt="" />
	</div>
</div>
