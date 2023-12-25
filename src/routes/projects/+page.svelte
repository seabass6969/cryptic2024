<script lang="ts">
	import Cmatrix from "$lib/components/cmatrix.svelte";
	import { projectlist } from "$lib/projects";
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
		<span class="title">projects: </span>
		</div>
		<div class="cards">
		{#each projectlist as project}
		   <div class="card">
				<a href={project.link}>
					<img src={project.src} alt="" class="imagesize">
					<div class="description">{project.description}</div>
				</a>
		   </div>
		{/each}
		</div>
	<div class="">
		<span>List of my legacy project:</span><br />
		<a class="leglink" href="https://covid.cephas.monster">Covid tracker</a
		><br />
		<a class="leglink" href="https://2022.cephas.monster">2022 Website</a>
		<br>
		<a class="leglink" href="https://2023.cephas.monster">2023 Website</a>
	</div>

	</div>
{/if}

<style lang="scss">
	.bigdiv {
		width: calc(100vw - 20px);
		font-weight: 400;
		padding: 10px;
		z-index: 9999;
		font-size: 2rem;
	}
	.imagesize {
		width: 30vw;
		@media (max-width: 600px) {
			width: 70vw;
		}
	}
	.description {
		font-size: 1rem;
	}
	.cards {
		display: grid;
		// grid-auto-flow:column;
		grid-template-columns: repeat( auto-fit, minmax(35vw, 1fr) );
		@media (max-width: 600px) {
			grid-template-columns: repeat( auto-fit, minmax(75vw, 1fr) );
		}
	}
	.card {
		padding: 1vw;
		margin: 1vw;
	background: rgba( 255, 255, 255, 0.25 );
	box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
	backdrop-filter: blur( 6.5px );
	-webkit-backdrop-filter: blur( 6.5px );
	border-radius: 10px;
	border: 1px solid rgba( 255, 255, 255, 0.18 );
	}
	.sameline {
		display: flex;
		align-items: center;
	}
	.title {
		margin-left: 5px;
	}
</style>
