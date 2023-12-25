<script>
	import { fade } from "svelte/transition";
	import "../app.scss";
</script>

<svelte:head>
	<title>cephas@localhost</title>
</svelte:head>
<div transition:fade>
<slot />
</div>
