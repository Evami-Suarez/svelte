<script>
	import { pageTabs } from '../../stores/userVariables';

	const tabs = [
		{ name: 'home', label: 'Home' },
		{ name: 'aboutUs', label: 'About Us' },
		{ name: 'features', label: 'Features' },
		{ name: 'pricing', label: 'Pricing' },
		{ name: 'contactUs', label: 'Contact Us' }
	];

	let menuOpen = false;
</script>

<nav
	class="sticky top-0 z-50 flex items-center justify-between p-4 px-[90px] backdrop-blur-2xl
"
>
	<div>
		<img class="w-[6rem] h-400" src="/veent-logo.svg" alt="veent" />
	</div>

	<ul class="hidden space-x-4 md:flex">
		{#each tabs as tab}
			<li>
				<button
					on:click={() => ($pageTabs = tab.name)}
					class="mx-[20px] border-b-[3px] pt-[8px] text-black transition-all
                    {$pageTabs === tab.name
						? 'border-[#D12F2B] text-[#D12F2B]'
						: 'border-transparent text-[#D12F2B] hover:border-[#D12F2B] hover:text-[#D12F2B]'}"
				>
					{tab.label}
				</button>
			</li>
		{/each}
	</ul>

	<!-- Mobile Menu -->
	<ul
		class="absolute left-0 top-[60px] flex w-full transform flex-col items-center bg-white shadow-md transition-transform duration-300 md:hidden"
		style="transform: translateY({menuOpen ? '0' : '-100%'})"
	>
		{#each tabs as tab}
			<li class="w-full border-b text-center">
				<button
					on:click={() => {
						$pageTabs = tab.name;
						menuOpen = false;
					}}
					class="block w-full py-4 text-lg text-black transition-all"
				>
					{tab.label}
				</button>
			</li>
		{/each}
	</ul>

	<div>
		<a href="https://www.veent.io/login/">
			<button
				class="rounded-[10px] bg-[#D12F2B] px-[40px] py-2 text-[16px] font-bold text-white transition hover:bg-[#990C08]"
			>
				Sign In
			</button>
		</a>
	</div>
</nav>
