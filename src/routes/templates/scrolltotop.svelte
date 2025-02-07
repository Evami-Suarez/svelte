<script>
    import { onMount } from "svelte";

    let showButton = false;

    onMount(() => {
        const handleScroll = () => {
            showButton = window.scrollY > 200;
        };

        window.addEventListener("scroll", handleScroll);
        return () => window.removeEventListener("scroll", handleScroll);
    });

    function scrollToTop() {
        window.scrollTo({ top: 0, behavior: "smooth" });
    }
</script>

<div
    class="fixed bottom-5 right-5 z-50 transition-all duration-300 ease-in-out 
          transform scale-0 opacity-0"
    class:scale-100={showButton} 
    class:opacity-100={showButton}
>
    <button
        on:click={scrollToTop}
        class="flex items-center justify-center w-12 h-12 rounded-full bg-red-600 
               text-white shadow-lg hover:bg-red-700 focus:outline-none"
    >
        ▲
    </button>
</div>
