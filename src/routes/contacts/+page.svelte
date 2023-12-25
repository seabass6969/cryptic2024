<script lang="ts">
	import Cmatrix from "$lib/components/cmatrix.svelte";
	import { sleep } from "$lib/sleep";
	import { onMount } from "svelte";
	let enable = true;
	onMount(async () => {
		await sleep(2200);
		enable = false;
	});
</script>

{#if enable}
	<Cmatrix />
{:else}
	<div class="bigdiv">
		<div class="sameline">
		<a href="/" class="material-symbols-outlined">
		home
		</a>
		contacts:
		</div>
	<div class="normalfont center">
		<a href="https://github.com/seabass6969/"
			><img
				src="/assets/GitHub.svg"
				alt="github icon"
				width="190px"
			/></a
		>
		<a href="https://gitlab.com/seabass6969group">
			<img
				class=""
				src="/assets/gitlab.svg"
				alt="gitlab logo"
				width="190px"
			/>
		</a>
		<a href="https://discord.com/users/665915259848228884">
			<img
				class=""
				src="/assets/Discord.svg"
				alt="Discord logo"
				width="208px"
			/>
		</a>
	</div>

	</div>
{/if}

<style lang="scss">
	.bigdiv {
		width: calc(100vw - 20px);
		height: calc(100vh - 20px);
		font-weight: 400;
		padding: 10px;
		position: fixed;
		z-index: 9999;
		font-size: 2rem;
	}
	.sameline {
		display: flex;
		align-items: center;
	}
</style>
