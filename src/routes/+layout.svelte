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
		transition: background-color 0.3s ease, color 0.3s ease;
	}

	:global(.light-mode body) {
		background-color: #F2F0EF;
	}

	/* Profile picture shadow only in light mode */
	:global(.light-mode .profile-shadow) {
		box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
	}

	/* Override all white text to dark in light mode */
	:global(.light-mode .text-white) {
		color: #66615E !important;
	}

	/* Override all gray text to medium dark in light mode */
	:global(.light-mode .text-gray-300),
	:global(.light-mode .text-gray-400) {
		color: #5a5654 !important;
	}

	/* Override divider background */
	:global(.light-mode .bg-white) {
		background-color: #5a5654 !important;
	}

	/* Override hover states */
	:global(.light-mode .hover\:text-white:hover) {
		color: #66615E !important;
	}

	:global(.light-mode .hover\:border-white:hover) {
		border-color: #66615E !important;
	}

	/* Override border colors */
	:global(.light-mode .border-gray-400) {
		border-color: #5a5654 !important;
	}

	/* Override marker colors */
	:global(.light-mode ul li::marker) {
		color: #66615E !important;
	}
</style>

{@render children()}