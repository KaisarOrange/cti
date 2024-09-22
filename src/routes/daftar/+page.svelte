<script>
	import emailjs from 'emailjs-com';
	import { goto } from '$app/navigation';
	import { PUBLIC_PUBLIC, PUBLIC_SERVICE, PUBLIC_TEMPLATE } from '$env/static/public';

	let page = 0;

	let formData = {
		name: '',
		email: '',
		message: '',
		usia: null,
		kelamin: '',
		lulus: null,
		phone: '',
		tinggi: null,
		badan: null,
		alamat: '',
		kelurahan: '',
		status: '',
		kecamatan: '',
		kabupaten: '',
		provinsi: '',
		kode: null,
		cabang: '',
		program: ''
	};
	let isSubmitting = false;
	let successMessage = '';
	let errorMessage = '';

	const sendEmail = async () => {
		isSubmitting = true;

		try {
			const result = await emailjs.send(PUBLIC_SERVICE, PUBLIC_TEMPLATE, formData, PUBLIC_PUBLIC);
			console.log(formData);
			successMessage = 'Email sent successfully!';
			setTimeout(() => {
				// Code to be executed after 1 second (1000 milliseconds)
				goto('/');
			}, 2000);
			formData = {
				name: '',
				email: '',
				message: '',
				usia: 0,
				kelamin: '',
				lulus: 0,
				phone: '',
				tinggi: 0,
				alamat: '',
				kelurahan: '',
				kecamatan: '',
				kabupaten: '',
				provinsi: '',
				kode: 0,
				badan: 0,
				status: '',
				cabang: '',
				program: ''
			};
		} catch (error) {
			errorMessage = 'Error sending email. Please try again later.';
			console.error('EmailJS error:', error);
		} finally {
			isSubmitting = false;
		}
	};
</script>

<div class="flex flex-col lg:flex-row items-center justify-center gap-5 h-screen">
	<div class="m-auto flex justify-center items-center bg-white h-screen flex-1">
		<img class="w-1/2 h-auto" src="logo.png" alt="" />
	</div>
	<div class="bg-blue-200 py-5 px-20 lg:w-1/2 flex flex-col items-center justify-center">
		<div
			class="bg-white w-80 px-5 py-2 lg:w-3/4 flex flex-col items-center justify-center rounded-md"
		>
			<h2 class="font-semibold">Daftar</h2>
			<form class="w-full flex flex-col gap-3 mt-10" on:submit|preventDefault={sendEmail}>
				{#if page === 0}
					<div class="flex flex-col">
						<label for="subsidiary">Cabang</label>
						<select
							class="border-2 rounded-md px-2 py-1"
							id="subsidiary"
							bind:value={formData.cabang}
							required
						>
							<option value="" disabled selected>Pilih cabang</option>
							<option value="Malang">Malang</option>
							<option value="Gresik">Gresik</option>
							<option value="Tuban">Tuban</option>
							<option value="Mataram">Mataram</option>
							<option value="Tegal">Tegal</option>
						</select>
					</div>
					<div class="flex flex-col">
						<label for="subsidiary">Program</label>
						<select
							class="border-2 rounded-md px-2 py-1"
							id="program"
							bind:value={formData.program}
							required
						>
							<option value="" disabled selected>Pilih program</option>
							<option value="Ground Handling">Ground Handling (Kerja)</option>
							<option value="Ground Handling">Ground Handling (Magang)</option>
							<option value="Pertanian">Pertanian (Kerja)</option>
							<option value="Pertanian">Pertanian (Magang)</option>
						</select>
					</div>
					<div class="flex flex-col">
						<label for="name">Nama lengkap</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="name"
							type="text"
							bind:value={formData.name}
							required
						/>
					</div>

					<div class="flex flex-col">
						<label for="email">Email</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="email"
							type="email"
							bind:value={formData.email}
							required
						/>
					</div>

					<div class="flex flex-col">
						<label for="email">Usia</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="usia"
							type="number"
							min="0"
							bind:value={formData.usia}
							required
						/>
					</div>

					<div class="flex flex-col">
						<label for="email">Jenis kelamin</label>
						<div class="flex items-center gap-2">
							<input
								class="border-2 rounded-md px-2 py-1"
								id="kelamin1"
								name="kelamin"
								type="radio"
								min="0"
								value="laki-laki"
								bind:group={formData.kelamin}
								required
							/>
							<label for="">laki-laki</label>
							<input
								class="border-2 rounded-md px-2 py-1"
								id="kelamin2"
								name="kelamin"
								type="radio"
								min="0"
								value="perempuan"
								bind:group={formData.kelamin}
								required
							/>
							<label for="">perempuan</label>
						</div>
					</div>
					<div class="flex flex-col">
						<label for="email">Status</label>
						<div class="flex items-center gap-2">
							<input
								class="border-2 rounded-md px-2 py-1"
								id="status1"
								name="status"
								type="radio"
								value="single"
								bind:group={formData.status}
								required
							/>
							<label for="">single</label>
							<input
								class="border-2 rounded-md px-2 py-1"
								id="status2"
								name="status"
								type="radio"
								value="menikah"
								bind:group={formData.status}
								required
							/>
							<label for="">menikah</label>
						</div>
					</div>
				{/if}
				{#if page === 1}
					<div class="flex flex-col">
						<label for="email">Tahun lulus sekolah</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="lulus"
							type="number"
							min="0"
							bind:value={formData.lulus}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="email">No. HP Aktif</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="phone"
							type="number"
							minlength="6"
							bind:value={formData.phone}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="email">Tinggi badan</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="tinggi"
							type="number"
							min="0"
							bind:value={formData.tinggi}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="email">Berat badan</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="badan"
							type="number"
							min="0"
							bind:value={formData.badan}
							required
						/>
					</div>
				{/if}
				{#if page === 2}
					<div class="flex flex-col">
						<label for="email">Alamat domisili</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="alamat"
							type="text"
							bind:value={formData.alamat}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="kelurahan">Kelurahan</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="kelurahan"
							type="text"
							bind:value={formData.kelurahan}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="kelurahan">Kecamatan</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="kecamatan"
							type="text"
							bind:value={formData.kecamatan}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="kelurahan">Kabupaten</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="kabupaten"
							type="text"
							bind:value={formData.kabupaten}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="kelurahan">Provinsi</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="provinsi"
							type="text"
							bind:value={formData.provinsi}
							required
						/>
					</div>
					<div class="flex flex-col">
						<label for="kelurahan">Kode pos</label>
						<input
							class="border-2 rounded-md px-2 py-1"
							id="kode"
							type="number"
							bind:value={formData.kode}
							required
						/>
					</div>
				{/if}

				{#if page < 2}
					<div class="m-auto">
						<button
							on:click={() => page--}
							disabled={page === 0}
							class="disabled:bg-slate-300 border px-2 py-1 mt-5 rounded-md bg-[#0162AE] text-white font-semibold"
							type="submit"
						>
							kembali
						</button>
						<button
							class="disabled:bg-slate-300 border px-2 py-1 mt-5 rounded-md bg-[#0162AE] text-white font-semibold"
							on:click={() => page++}
						>
							selanjutnya
						</button>
					</div>
				{/if}
				{#if page === 2}
					<div class="flex gap-1">
						<button
							on:click={() => page--}
							disabled={page === 0}
							class="disabled:bg-slate-300 border px-2 py-1 mt-5 rounded-md bg-[#0162AE] text-white font-semibold"
							type="submit"
						>
							kembali
						</button>
						<button
							class="border w-full px-2 py-1 mt-5 rounded-md bg-[#0162AE] text-white font-semibold"
							type="submit"
							disabled={isSubmitting}
						>
							{isSubmitting ? 'Sending...' : 'Daftar'}
						</button>
					</div>
				{/if}

				{#if successMessage}
					<p>{successMessage}</p>
				{/if}

				{#if errorMessage}
					<p style="color: red;">{errorMessage}</p>
				{/if}
			</form>
		</div>
	</div>
</div>
