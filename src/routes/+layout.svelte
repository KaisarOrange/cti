<script>
	let isOpen = false;
	import '../app.css';
</script>

<div class="bg-blue-200">
	<nav class="bg-white">
		<div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8">
			<div class="relative flex items-center justify-between h-16">
				<!-- Mobile Menu Button -->
				<div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
					<button
						class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-[#0162AE] focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
						aria-expanded="false"
						on:click={() => (isOpen = !isOpen)}
					>
						<svg
							class="block h-6 w-6"
							xmlns="http://www.w3.org/2000/svg"
							fill="none"
							viewBox="0 0 24 24"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M4 6h16M4 12h16m-7 6h7"
							/>
						</svg>
					</button>
				</div>

				<!-- Logo -->
				<div class="flex-1 flex items-center justify-center sm:items-stretch sm:justify-start">
					<div class="flex-shrink-0">
						<a href="/" class="text-white text-2xl font-bold"
							><img class="w-52" src="logo.png" alt="" srcset="" /></a
						>
					</div>
				</div>

				<!-- Desktop Menu -->
				<div class="hidden sm:block sm:ml-6">
					<div class="flex space-x-4">
						<a
							href="/"
							class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white px-3 py-2 rounded-md text-sm font-medium"
							>Beranda</a
						>
						<a
							href="/about"
							class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white px-3 py-2 rounded-md text-sm font-medium"
							>Tentang Kami</a
						>
						<a
							href="/visi"
							class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white block px-3 py-2 rounded-md text-base font-medium"
							>Vision & Philosophy</a
						>
						<!-- <a
							href="/filosofi"
							class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white px-3 py-2 rounded-md text-sm font-medium"
							>Filosofi</a
						> -->
					</div>
				</div>
			</div>
		</div>

		<!-- Mobile Menu Dropdown -->
		{#if isOpen}
			<div class="sm:hidden">
				<div class="px-2 pt-2 pb-3 space-y-1">
					<a
						href="/"
						class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white block px-3 py-2 rounded-md text-base font-medium"
						>Beranda</a
					>
					<a
						href="/about"
						class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white block px-3 py-2 rounded-md text-base font-medium"
						>Tentang Kami</a
					>
					<a
						href="/visi"
						class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white block px-3 py-2 rounded-md text-base font-medium"
						>Vision & Philosophy</a
					>
					<!-- <a
						href="/filosofi"
						class="text-[#0162AE] hover:bg-[#0162AE] hover:text-white block px-3 py-2 rounded-md text-base font-medium"
						>Filosofi</a
					> -->
				</div>
			</div>
		{/if}
	</nav>
	<div class="">
		<slot />
	</div>
	<footer class="bg-white p-10">
		<img class="w-2/3 md:w-1/6 mb-2" src="logo.png" alt="" srcset="" />
		<div class="md:ml-16">
			<h2 class="font-bold">Address:</h2>
			<h3>
				Tirtasani Sports Center, Tirtasani Royal Resot, Jalan Raya Perusahaan, Malang Regency, East
				Java
			</h3>
			<h2 class="font-bold">Email:</h2>
			<h3>cahayatitianinsantama@gmail.com</h3>
		</div>
	</footer>
</div>
