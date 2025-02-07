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
	let activeTab = '';
  </script>
  
  <nav class="sticky z-50 flex items-center justify-between p-3 pt-5 bg-transparent">
	<!-- Left side (Logo) -->
	<img class="h-10 w-[6rem] sm:w-[8rem]" src="/veent-logo.svg" alt="veent" />
  
	<!-- Desktop Navigation -->
	<div class="hidden sm:flex flex-1 justify-center">
	  <ul class="flex space-x-10">
		{#each tabs as tab}
		  <li>
			<button
			  on:click={() => ($pageTabs = tab.name)}
			  class="border-b-2 pb-1 transition-all
				{$pageTabs === tab.name
				  ? 'border-red-600 text-red-600'
				  : 'border-transparent text-gray-700 hover:border-red-600 hover:text-red-600'}"
			>
			  {tab.label}
			</button>
		  </li>
		{/each}
	  </ul>
	</div>
  
	<!-- Sign In Button (Right Aligned) -->
	<a href="https://www.veent.io/login/" class="hidden sm:block">
	  <button class="rounded-lg bg-red-600 px-6 py-2 text-white font-bold transition hover:bg-red-700">
		Sign In
	  </button>
	</a>
  
	<!-- Mobile Menu Button -->
	<button
	  on:click={() => (menuOpen = !menuOpen)}
	  class="sm:hidden p-2 text-gray-700 hover:bg-gray-200 rounded-md focus:outline-none"
	>
	  {#if menuOpen}
		<!-- X Icon -->
		<svg class="block size-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
		  <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
		</svg>
	  {:else}
		<!-- Hamburger Icon -->
		<svg class="block size-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
		  <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
		</svg>
	  {/if}
	</button>
  
	<!-- Mobile Menu -->
	<div class="{menuOpen ? 'block' : 'hidden'} sm:hidden absolute top-16 right-0 w-full bg-red-600 shadow-md">
	  <ul class="flex flex-col space-y-2 p-4">
		{#each tabs as tab}
		  <li>
			<button
			  on:click={() => { activeTab = tab.name; $pageTabs = tab.name; }}
			  class="block w-full text-left py-2 px-4 text-white bg-red-600 border-b-1 transition border-slide
				{activeTab === tab.name ? 'border-white' : 'border-transparent hover:border-white'}"
			>
			  {tab.label}
			</button>
		  </li>
		{/each}
		<!-- Sign In Button (Only in Mobile Menu) -->
		<li class="mt-2">
		  <a href="https://www.veent.io/login/">
			<button class="w-full rounded-lg bg-white px-6 py-2 text-red-600 font-bold border border-transparent transition hover:bg-gray-200 hover:border-white">
			  Sign In
			</button>
		  </a>
		</li>
	  </ul>
	</div>
  </nav>
  