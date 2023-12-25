<script lang="ts">
	import { typewriter } from "$lib/animation";
	import Backgroundcephas from "$lib/components/Backgroundcephas.svelte";
	import Cmatrix from "$lib/components/cmatrix.svelte";
	import Loadingbarbackground from "$lib/components/loadingbarbackground.svelte";
	import { sleep } from "$lib/sleep";
	import { onMount } from "svelte";
	import { cubicOut } from "svelte/easing";
	import { spring, tweened } from "svelte/motion";
	let enable = true;

    const valueprogress = tweened(0, {duration: 1000,easing: cubicOut})
	onMount(async () => {
		await sleep(2500);
		enable = false;
        while(true){
            await sleep(1000)
            valueprogress.set(Math.random())
        }
	});
	let coords = spring({ x: 50, y: 50 }, { stiffness: 0.2, damping: 0.25 });
	let clientHeight: number = 0;
	let clientWidth: number = 0;

</script>

<svelte:window
	bind:innerHeight={clientHeight}
	bind:innerWidth={clientWidth}
	on:mousemove={(e) => coords.set({ x: e.clientX, y: e.clientY })}
/>
{#if enable}
	<Cmatrix />
{:else}
	<div class="bigdiv">
		<span class="sameline"
			>cephas@localhost &nbsp;&nbsp;<span class="green">~></span></span
		>
		<span class="sameline">
			Hello <div class="wavehand">👋</div></span
		>
		<span in:typewriter={{ speed: 4 }}>Choose an option below:</span>
		<div class="gridcentered">
   <div class="card">
			<a href="/projects" in:typewriter={{ speed: 2 }} class="hover"
				>Project</a
			>
			<progress
                class="randommovement " 
                value={$coords.x} 
                max={clientWidth}
			></progress>
   </div>
   <div class="card">
			<a href="/contacts" in:typewriter={{ speed: 2 }} class="hover"
				>Social</a
			>
			<progress
				class="randommovement"
				value={$coords.y}
				max={clientHeight}
			></progress>
   </div>
   <div class="card">
			<a href="/skills" in:typewriter={{ speed: 2 }} class="hover"
				>Skills</a
			>
			<progress
				class="randommovement"
                value={$valueprogress}
			></progress>
   </div>
		</div>
	</div>
	<Backgroundcephas />
	<Loadingbarbackground />
{/if}

<style lang="scss">
	.randommovement {
		width: 20vw;
	}
	.bigdiv {
		width: calc(100vw - 20px);
		height: calc(100vh - 20px);
		font-weight: 400;
		padding: 10px;
		position: fixed;
		z-index: 9999;
		font-size: 2rem;
		@media (max-width: 600px) {
			font-size: 1rem;
		}

	}
	.green {
		color: rgb(45, 218, 45);
	}
	.sameline {
		display: flex;
	}
	.gridcentered {
		display: grid;
		width: 100%;
		align-items: center;
		justify-items: center;
		grid-template-columns: auto auto auto;
		font-size: 2.5rem;
	}
	.hover {
        padding: 2px;
		color: aquamarine;
        background-image: linear-gradient($third-color, $third-color);
        background-repeat: no-repeat;
        background-size: 10px 100%;
        background-position: 0 0;
		@media (max-width: 600px) {
			font-size: 1.4rem;
		}
        transition: 
            background-size 0.3s,
            background-position 0.3s 0.6s;
	}
	.hover:hover{
        background-size: 100% 100%;
        background-position: 100% 0;
        transition: 
            background-size 0.3s,
            background-position 0.3s 0.6s;
	}

	.wavehand {
		animation: infinite wavehand 5000ms;
        width: fit-content;
	}
	@keyframes wavehand {
		0% {
			transform: rotate(0deg);
		}
		5% {
			transform: rotate(20deg);
		}
		10% {
			transform: rotate(0deg);
		}
		15% {
			transform: rotate(20deg);
		}
		20% {
			transform: rotate(0deg);
		}
		100% {
			transform: rotate(0deg);
		}
	}
    .card {
        margin: 2vw;
        padding: 2vw;
	background: rgba( 255, 255, 255, 0.25 );
	box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
	backdrop-filter: blur( 6.5px );
	-webkit-backdrop-filter: blur( 6.5px );
	border-radius: 10px;
	border: 1px solid rgba( 255, 255, 255, 0.18 );
    }
</style>
