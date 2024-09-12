<script>
	import '../app.css';
</script>

<div class="bg-blue-300 min-h-screen">
	<nav class="bg-white flex items-center justify-between p-5">
		<img class="w-1/6" src="logo.png" alt="" srcset="" />
		<div class="flex items-center justify-center gap-20 flex-1">
			<button class="p-2 active:bg-orange-400 active:text-orange-700">Beranda</button>
			<button>Profil</button>
			<button>Program</button>
			<button>Hubungi Kami</button>
		</div>
	</nav>
	<slot />
</div>
