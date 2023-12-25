<script>
	import { fade } from "svelte/transition";
	import "../../app.scss";
</script>

<div transition:fade>
    <slot />
</div>
