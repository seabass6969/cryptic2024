<script lang="ts">
	import { cephas } from "$lib/funkytext";
	import { sleep } from "$lib/sleep";
	import { onMount } from "svelte";
	import { cubicOut } from "svelte/easing";
	import { tweened } from "svelte/motion";
	import { fade, fly } from "svelte/transition";
	import Backgroundcephas from "./Backgroundcephas.svelte";
	function getTextSize() {
		let text = document.createElement("span");
		document.body.appendChild(text);
		text.style.fontSize = 16 + "px";
		text.style.height = "auto";
		text.style.width = "auto";
		text.style.position = "absolute";
		text.style.whiteSpace = "no-wrap";
		text.style.fontWeight = "400";
		text.innerHTML = "1";

		let width = Math.ceil(text.clientWidth);
		let height = Math.ceil(text.clientHeight);
		document.body.removeChild(text);
		return { Width: width, Height: height };
	}
	let arrayOfSymbol: string[][] = [[]];
	let clientHeight: number = 0;
	let clientWidth: number = 0;
	console.log(getTextSize());
	function windowResize() {
		let widthItem = Math.floor(clientWidth / getTextSize().Width);
		let HeightItem =
			Math.floor((clientHeight - 20) / getTextSize().Height) - 2;
		console.log({ widthItem: widthItem, HeightItem: HeightItem });
		console.log({ clientWidth: clientWidth, clientHeight: clientHeight });
		arrayOfSymbol = [];
		for (let index = 0; index < HeightItem; index++) {
			let items: string[] = [];
			for (let y = 0; y < widthItem; y++) {
				let stringTobePushed =
					randomSymbol[
						Math.floor(Math.random() * randomSymbol.length)
					];
				items.push(stringTobePushed);
			}
			arrayOfSymbol.push(items);
		}
		console.log(arrayOfSymbol);
	}
	const randomSymbol = "!@#$%^&*()        ";
	let enable = false;

    const valueprogress = tweened(0, {duration: 1000,easing: cubicOut})
	onMount(async () => {
		windowResize();
		enable = true;
        await sleep(1000)
        valueprogress.set(1)
	});
</script>

<svelte:window
	on:resize={windowResize}
	bind:innerHeight={clientHeight}
	bind:innerWidth={clientWidth}
/>
<div class="matrix">
	{#if enable}
		<div in:fly={{ y: -100, duration: 2000 }} out:fly={{y: 200, duration: 1000}}>
			{#each arrayOfSymbol as a}
				<span class="nofeature">
					{#each a as b}
						{#key b}
							<span class="green">{b}</span>
						{/key}
					{/each}
				</span>
				<br />
			{/each}
		</div>
	{/if}
</div>

<div class="floatingdiv">
<progress value={$valueprogress} class="progress"></progress>
</div>
<Backgroundcephas />
<style lang="scss">
	.matrix {
		background-color: $base-color;
		width: calc(100vw - 20px);
		height: calc(100vh - 20px);
		font-weight: 400;
		padding: 10px;
	}
	.nofeature {
		font-size: 16px;
		font-feature-settings: "lnum1" on;
	}
    .floatingdiv {
        position: absolute;
        top: 0;
        left: 0;
        padding: 50px;
        width: calc(100vw - 100px);
        height: calc(100vh - 100px);
        display: flex;
        justify-content: center;
        font-size: xxx-large;
        z-index: 99;
    }
    .progress {
        width: 50vw;
    }
    .green {
        color: rgba(0, 255, 0, 0.193);
    }
</style>
