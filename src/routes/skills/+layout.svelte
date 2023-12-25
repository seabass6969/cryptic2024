<script>
	import { fade } from "svelte/transition";
	import "../../app.scss";
</script>

<svelte:head>
	<title>Skills</title>
	<meta property="og:title" content="Cephas - Skills" />
</svelte:head>
<div transition:fade>
    <slot />
</div>
