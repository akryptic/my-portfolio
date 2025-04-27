<script lang="ts">
	import Footer from '$lib/Footer.svelte';
	import Header from '$lib/Header.svelte';
	import '../styles/app.scss';

	let { children } = $props();
</script>

<svelte:head>
	<meta name="title" content="Anil Kumar" />
	<meta name="description" content="Indie self-taught web developer" />
	<meta
		name="keywords"
		content="anil, kumar, indie developer, developer, web developer, freelancer"
	/>
	<meta name="robots" content="index, follow" />
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<meta name="language" content="English" />
	<meta name="revisit-after" content="2 days" />
	<meta name="author" content="Anil Kumar" />

	<script type="application/ld+json">
		{
			"@context": "https://schema.org",
			"@type": "Person",
			"name": "Anil Kumar",
			"url": "https://ardentkilnfire.xyz",
			"jobTitle": "Software Developer",
			"sameAs": ["https://twitter.com/akryptic0", "https://github.com/akryptic"]
		}
	</script>
</svelte:head>

<Header />
<main>
	{@render children()}
</main>
<Footer />

<style>
	main {
		display: grid;
		grid-template-columns: 1fr;
		padding-bottom: 2.4rem;
	}

	@media only screen and (min-width: 600px) {
		main {
			grid-template-columns: 1fr 1fr;
			gap: 2.4rem;
			width: fit-content;
			margin: auto;
			max-width: 1280px;
		}
	}
</style>
