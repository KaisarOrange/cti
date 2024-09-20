<script>
	import { fade, slide } from 'svelte/transition';
	import { onMount } from 'svelte';

	let divElement2; // reference to the div
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

		observer.observe(divElement2); // start observing the div

		return () => {
			observer.disconnect(); // cleanup when the component is destroyed
		};
	});
</script>

<div class="target2 min-h-screen" bind:this={divElement2}>
	{#if isInView}
		<div
			in:slide={{ duration: 2000 }}
			class="flex flex-col items-center gap-10 justify-center pb-20 m-auto md:w-5/6"
		>
			<div class="flex flex-col md:flex-row items-center justify-between gap-5">
				<div class="bg-white p-5 rounded-md">
					<div class="h-[200px] lg:h-[300px] w-[330px] lg:w-[580px] overflow-hidden">
						<img class="h-[200px] lg:h-[300px] w-[370px] lg:w-[580px]" src="ground.png" alt="" />
					</div>
					<h2 class="text-orange-400 font-extrabold mt-2 text-3xl">Ground Handling</h2>
					<h3 class="text-orange-400 font-bold mt-2">Proyeksi gaji</h3>
					<h4 class="text-[#0162AE] font-semibold mt-1">Rp. 10.000.000 s/d Rp. 15.000.000</h4>
					<button class="w-full py-2 bg-[#0162AE] rounded-md mt-10 font-semibold text-white"
						>Daftar</button
					>
				</div>
				<div class="bg-white p-5 rounded-md">
					<div class="h-[200px] lg:h-[300px] w-[330px] lg:w-[580px] overflow-hidden">
						<img
							class="h-[200px] lg:h-[300px] w-[370px] lg:w-[580px]"
							src="agrikultur.png"
							alt=""
						/>
					</div>
					<h2 class="text-orange-400 font-extrabold mt-2 text-3xl">Agriculture</h2>
					<h3 class="text-orange-400 font-bold mt-2">Proyeksi gaji</h3>
					<h4 class="text-[#0162AE] font-semibold mt-1">Rp. 10.000.000 s/d Rp. 15.000.000</h4>
					<button class="w-full py-2 bg-[#0162AE] rounded-md mt-10 font-semibold text-white"
						>Daftar</button
					>
				</div>
			</div>
			<div class="bg-blue-300 flex w-full gap-5 p-2 rounded-sm">
				<div class="bg-white flex md:w-3/4 gap-10 p-2">
					<div class="h-[300px] w-3/4 overflow-hidden">
						<img class="h-[300px] w-[600px] object-cover object-left" src="gambar6.png" alt="" />
					</div>
					<div class="w-1/2 py-5 pr-2">
						<h2 class="text-3xl font-extrabold w-2/3 text-orange-400">
							Trusted by Japanese companies
						</h2>
						<p class="text-[#0162AE] mt-2">
							All the educational institutions we own, aim to produce comprehensively skilled and
							measurable workers. We also aspire to be a trusted institution by companies in Japan
							and contribute to the economic growth of these two friendly countries.
						</p>
						<!-- <p class="mt-10 text-[#0162AE]">Vol Smaak | Vol Vitamines | Volop Genieten</p> -->
					</div>
				</div>
				<div class="bg-blue-100 w-2/5">
					<div class="p-2">
						<img class="w-full" src="gambar5.png" alt="" />
						<div class="p-5">
							<h2 class="text-3xl font-extrabold text-orange-400">Company Strategy</h2>
							<!-- <h2 class="mt-10 text-[#0162AE]">Benodigdheden</h2> -->
							<ul class="list-disc pl-5 text-[#0162AE] mt-2">
								<li>Providing prospective students with affordable training and departure costs</li>
								<li>Ensuring accessible and adequate learning and sports facilities.</li>
								<li>
									Monitoring and evaluating the performance of our trainees while they work at
									Japanese companies
								</li>
							</ul>
						</div>
					</div>
				</div>
			</div>
		</div>
	{/if}
</div>
