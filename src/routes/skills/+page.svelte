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
			<a href="/" class="material-symbols-outlined"> home </a>
			skills:
		</div>
		<p>
			Programming languages:
			<br />
			<img
				src="https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E"
				alt=""
			/><img
				src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00"
				alt=""
			/>
		</p>
		<p class="subtitle">
			Used editor/platform:<br />
			<img
				src="https://img.shields.io/badge/NeoVim-%2357A143.svg?&style=for-the-badge&logo=neovim&logoColor=white
"
				alt=""
			/><img
				src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black"
				alt=""
			/><img
				src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/Raspberry%20Pi-A22846?style=for-the-badge&logo=Raspberry%20Pi&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/tmux-1BB91F?style=for-the-badge&logo=tmux&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=Cloudflare&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/Heroku-430098?style=for-the-badge&logo=heroku&logoColor=white"
				alt=""
			/><img
				src="https://img.shields.io/badge/gitlab-black?style=for-the-badge&logo=gitlab"
				alt=""
			/>
		</p>
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
</style>
