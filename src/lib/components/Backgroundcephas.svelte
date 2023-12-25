<script>


	import { cephas } from "$lib/funkytext";
	import { fade } from "svelte/transition";

</script>

<div class="floatingdivgrid">
    <div >
    {#each cephas as c}
        <pre class="notopandbottom" in:fade>{c}</pre>
    {/each}
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
        align-items: center;
        justify-content: center;
        z-index: 0;
    }
    .notopandbottom {
        margin: 0;
        font-size: 27px;
        color: rgba(255, 0, 0, 0.685);
		@media (max-width: 600px) {
			font-size: 14px;
		}

    }
</style>