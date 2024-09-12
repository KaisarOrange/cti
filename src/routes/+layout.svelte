<script>
	import '../app.css';
</script>

<div class="bg-blue-300 min-h-screen">
	<nav class="bg-white flex items-center justify-between p-5">
		<img class="w-1/6" src="logo.png" alt="" srcset="" />
		<div class="flex items-center justify-center gap-20 flex-1 text-[#0162AE] font-semibold">
			<button class="p-2 active:bg-orange-400 active:text-orange-700">Beranda</button>
			<button>Profil</button>
			<button>Program</button>
			<button>Hubungi Kami</button>
		</div>
	</nav>
	<slot />
	<footer class="bg-white p-10">
		<img class="w-1/6" src="logo.png" alt="" srcset="" />
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
