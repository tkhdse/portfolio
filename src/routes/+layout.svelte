<script lang="ts">
	import './layout.css';
	// import favicon from '$lib/assets/favicon.svg';
	import favicon from '$lib/assets/wave.webp';
	let { children } = $props();
</script>


<svelte:head>
	<link rel="icon" href={favicon} />
    <title>Tanish Khadse</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link href="https://fonts.googleapis.com/css2?family=Google+Sans+Code:ital,wght@0,300..800;1,300..800&family=Instrument+Sans:ital,wght@0,400..700;1,400..700&family=PT+Sans:ital,wght@0,400;0,700;1,400;1,700&display=swap" rel="stylesheet">

</svelte:head>

<style>
	:global(body) {
		background-color: #1a1a1a;
	}
</style>

{@render children()}
