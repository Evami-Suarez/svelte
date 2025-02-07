<script>
	import CirclesLeft from '$lib/circles-left.svelte';
	import CirclesRight from '$lib/circles-right.svelte';
	import HomeBlob from '$lib/homeBlob.svelte';
	import { onMount } from 'svelte';
  
  let isMobile = false;
  
  // Check window width on mount
  onMount(() => {
    isMobile = window.innerWidth < 640; // Adjust this value if needed
    window.addEventListener('resize', () => {
      isMobile = window.innerWidth < 640;
    });
  });

</script>

<div class:hidden={isMobile}>
	<CirclesLeft />
</div>

<div class:hidden={isMobile}>
	<CirclesRight />
</div>

<div class="flex min-h-screen items-center justify-center overflow-hidden">
	<div class="fade-down relative flex flex-col items-center justify-center text-center">
		<!-- Blob Positioned Behind Everything -->
		<div class="absolute inset-0 z-[-1] flex items-center justify-center" class:hidden={isMobile}>
			<HomeBlob />
		</div>

		<!-- Veent Image -->
		<img class="p-10 relative z-10 mt-[-160px] h-auto w-[350px] sm:w-[100px] md:w-[300px] lg:w-[400px] mx-auto" src="/veent.png" alt="veent" />

<!-- Main Text Content -->
<div class="text-[28px] font-bold text-[#D12F2B] text-center sm:text-[24px] text-shadow">
  Events, simplified.
</div>
<div class="sm:ml-3 sm:mr-3 mt-2 w-full sm:w-[600px] text-center sm:text-[16px] text-[20px] text-[#3E3C3D] mx-auto">
  Streamline event registration with Veent. Our user-friendly web app makes creating events a breeze. Packed with features and affordable pricing, Veent simplifies event management for everyone.
</div>


		<!-- Call-to-action Button -->
		<div class="my-[40px]">
			<a href="https://www.veent.io/signup">
				<button
					class="rounded-[10px] bg-[#D12F2B] px-[40px] py-2 text-[16px] font-bold text-white transition hover:bg-[#990C08]"
				>
					Sign up for free!
				</button>
			</a>
		</div>
	</div>
</div>
