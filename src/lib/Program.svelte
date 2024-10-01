<script>
	import { fade, slide } from 'svelte/transition';
	import { onMount } from 'svelte';
	import { goto } from '$app/navigation';

	let divElement2; // reference to the div
	let isInView = false;

	onMount(() => {
		const observer = new IntersectionObserver((entries) => {
			entries.forEach((entry) => {
				if (entry.isIntersecting) {
					isInView = true;
					console.log('Div is in view!');
				} else {
					// isInView = false;
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

<div class="target2 min-h-screen mt-10" bind:this={divElement2}>
	{#if isInView}
		<div
			in:slide={{ duration: 2000 }}
			class="flex flex-col items-center gap-10 justify-center pb-20 m-auto md:w-5/6 {isInView
				? ''
				: 'hidden'}"
		>
			<div class="flex flex-col md:flex-row items-center justify-between gap-5">
				<div class="bg-white p-5 rounded-md">
					<div class="h-[200px] lg:h-[300px] w-[330px] lg:w-[580px] overflow-hidden">
						<img class="h-[200px] lg:h-[300px] w-[370px] lg:w-[580px]" src="ground.png" alt="" />
					</div>
					<h2 class="text-orange-400 font-extrabold mt-2 text-3xl">Ground Handling</h2>
					<h3 class="text-orange-400 font-bold mt-2">Proyeksi gaji</h3>
					<h4 class="text-[#0162AE] font-semibold mt-1">Rp. 10.000.000 s/d Rp. 15.000.000</h4>
					<button
						on:click={() => goto('/daftar')}
						class="w-full py-2 bg-[#0162AE] rounded-md mt-10 font-semibold text-white"
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
					<h2 class="text-orange-400 font-extrabold mt-2 text-3xl">Pertanian</h2>
					<h3 class="text-orange-400 font-bold mt-2">Proyeksi gaji</h3>
					<h4 class="text-[#0162AE] font-semibold mt-1">Rp. 10.000.000 s/d Rp. 15.000.000</h4>
					<button
						on:click={() => goto('/daftar')}
						class="w-full py-2 bg-[#0162AE] rounded-md mt-10 font-semibold text-white"
						>Daftar</button
					>
				</div>
			</div>
			<div class="bg-blue-300 flex flex-col md:flex-row w-full gap-5 p-2 rounded-sm">
				<div class="bg-white flex flex-col md:flex-row md:w-3/4 md:gap-10 p-2">
					<div class="h-[300px] md:w-3/4 overflow-hidden">
						<img class="h-[300px] w-[600px] object-cover object-left" src="gambar6.png" alt="" />
					</div>
					<div class="md:w-1/2 py-5 pr-2">
						<h2 class="text-3xl font-extrabold md:w-2/3 text-orange-400">
							Dipercaya oleh perusahaan Jepang
						</h2>
						<p class="text-[#0162AE] mt-2">
							すべての教育機関は、総合的で測定可能なスキルを持つ労働者を育成することを目的としています。また、日本の企業から信頼され、この友好国二国の経済成長に貢献する機関となることを目指しています。
						</p>
						<p class="text-[#0162AE] mt-2 font-bold">
							Semua lembaga pendidikan yang kami miliki bertujuan untuk menghasilkan pekerja dengan
							keterampilan yang komprehensif dan terukur. Kami juga bercita-cita menjadi lembaga
							yang dipercaya oleh perusahaan-perusahaan di Jepang dan berkontribusi pada pertumbuhan
							ekonomi kedua negara bersahabat ini.
						</p>
						<!-- <p class="mt-10 text-[#0162AE]">Vol Smaak | Vol Vitamines | Volop Genieten</p> -->
					</div>
				</div>
				<div class="bg-blue-100 md:w-2/5">
					<div class="p-2">
						<img class="w-full" src="gambar5.png" alt="" />
						<div class="p-5">
							<h2 class="text-3xl font-extrabold text-orange-400">Strategi perusahaan</h2>
							<!-- <h2 class="mt-10 text-[#0162AE]">Benodigdheden</h2> -->
							<ul class="list-disc pl-5 text-[#0162AE] mt-2">
								<li>
									<div>
										見込み学生に対して、手頃なトレーニングおよび出発費用を提供し、月々の分割払いのオプショ
										ンを用意し、総額の50%を前金として提供します。残りの金額は、日本での就職後に分割払いが可
										能です。
									</div>
									<div class="font-bold">
										Memberikan calon siswa biaya pelatihan dan keberangkatan yang terjangkau.
									</div>
								</li>
								<li>
									<div>アクセスしやすく、適切な学習およびスポーツ施設を提供します。 。</div>
									<div class="font-bold">
										Memastikan fasilitas belajar dan olahraga yang aksesibel dan memadai.
									</div>
								</li>
								<li>
									<div>
										日本企業で働く学生のパフォーマンスを監視し、評価することが現在および今後の重点的な
										関心事です。
									</div>
									<div class="font-bold">
										Memantau dan mengevaluasi kinerja para peserta pelatihan kami saat mereka
										bekerja di perusahaan-perusahaan Jepang.
									</div>
								</li>
							</ul>
						</div>
					</div>
				</div>
			</div>
		</div>
	{/if}
</div>
