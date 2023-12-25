<script>
	import { fade } from "svelte/transition";
	import "../../app.scss";
</script>

<svelte:head>
	<title>Projects</title>
	<meta property="og:title" content="Cephas - Projects" />
</svelte:head>
<div transition:fade>
    <slot />
</div>
