<script>
	import { fade } from "svelte/transition";
	import "../../app.scss";
</script>

<svelte:head>
	<title>Contact</title>
	<meta property="og:title" content="Cephas - Contacts" />
</svelte:head>
<div transition:fade>
    <slot />
</div>
