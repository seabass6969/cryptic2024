<script>
	import { sleep } from "$lib/sleep";
	import { onMount } from "svelte";
	import { cubicOut } from "svelte/easing";
	import { tweened } from "svelte/motion";

    
    const valueprogress = tweened(0, {duration: 1000,easing: cubicOut})
    onMount(async ()=> {
        while(true){
            await sleep(1000)
            valueprogress.set(Math.random())
        }
    })
</script>

<div class="floatingdivgrid">
    <div >
        <progress value={$valueprogress}></progress>
    </div>
</div>

<style lang="scss">
    .floatingdivgrid {
        position: absolute;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        display: grid;
        grid-template-columns: auto;
        align-items:end;
        justify-content: center;
        z-index: 0;
    }
	progress {
        margin-bottom: 7vw;
		width: 70vw;
        height: 8vh;
	}
</style>