<script lang="ts">
	let blob: any;

	function handleFocus() {
		blob.classList.add('fast');
	}

	function toggleActive() {
		blob.classList.toggle('active');
	}
</script>

<div bind:this={blob} class="blob hidden sm:block"> <!-- Added hidden sm:block here -->
	<span></span>
	<span></span>
</div>

<style>
	.blob {
		--size: 900px;
		position: absolute;
		width: 40%;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		transition: 3s all;
		margin-top: -70px;
		animation:
			floating 4s ease-in-out infinite,
			scaling 3s ease-in-out infinite;
	}

	.blob > span {
		height: var(--size);
		width: var(--size);
		position: absolute;
		display: block;
		top: calc(50% - var(--size) / 2);
		transition: 1s all 0.13s ease-in-out;
	}

	.blob > span:first-child {
		left: calc(50% - var(--size) / 2);
	}

	.blob > span:last-child {
		right: calc(50% - var(--size) / 2);
	}

	.blob > span::before {
		content: '';
		display: block;
		opacity: 0.6;
		height: 100%;
		width: 100%;
		background-blend-mode: color;
		transition:
			2s all 0.25s ease-in-out,
			1.5s opacity,
			background-size 1.5s;
		animation: rotate 30s infinite linear both;

		mask:
			radial-gradient(circle, #000 50%, transparent 50%) 50% 50% / var(--size) var(--size),
			radial-gradient(circle, #000 50%, transparent 50%) 110% 10% / calc(var(--size) / 1.3)
				calc(var(--size) / 1.3),
			radial-gradient(circle, #000 50%, transparent 50%) -20% 20% / calc(var(--size) / 1.2)
				calc(var(--size) / 1.2),
			radial-gradient(circle, #000 50%, transparent 50%) 10% 110% / calc(var(--size) / 1.6)
				calc(var(--size) / 1.3);

		mask-repeat: no-repeat;
	}

	.blob > span:last-child::before {
		animation-direction: reverse;
	}

	.blob > span:first-child::before {
		background:
			radial-gradient(circle, #f5d5d4 50%, transparent 50%) 50% 50% / 0 0,
			linear-gradient(#f5d5d4, #de6d6a 40%) 50% 50% / 100% 100%;
		background-repeat: no-repeat;
	}

	.blob > span:last-child::before {
		background:
			radial-gradient(circle, #de6d6a 50%, transparent 50%) 50% 50% / 0 0,
			linear-gradient(#f5d5d4, #de6d6a) 50% 50% / 100% 100%;
		background-repeat: no-repeat;
	}

	@keyframes rotate {
		0% {
			transform: rotate(0deg);
		}

		100% {
			transform: rotate(365deg);
		}
	}

	@keyframes floating {
		0% {
			transform: translate(-50%, -50%) translateY(0);
		}
		50% {
			transform: translate(-50%, -50%) translateY(-20px);
		}
		100% {
			transform: translate(-50%, -50%) translateY(0);
		}
	}

	@keyframes scaling {
		0% {
			transform: translate(-50%, -50%) scale(1);
		}
		50% {
			transform: translate(-50%, -50%) scale(1.1);
		}
		100% {
			transform: translate(-50%, -50%) scale(1);
		}
	}
</style>
