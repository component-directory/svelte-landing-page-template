<script lang="ts">
	import Hero from '$lib/components/home/hero.svelte';
	import Features from '$lib/components/home/features.svelte';
	import Faqs from '$lib/components/home/faqs.svelte';
	import Metrics from '$lib/components/home/metrics.svelte';
	import Testimonials from '$lib/components/home/testimonials.svelte';
	import Technologies from '$lib/components/home/technologies.svelte';
</script>

<svelte:head>
	<title>Free Full-Stack Svelte Landing Page Template – Open Source</title>
	<meta
		name="description"
		content="Download a fully responsive, open-source landing page template built with Svelte 5 + ShadCN. Works seamlessly with full-stack apps, SaaS projects, and demos."
	/>
</svelte:head>

<Hero />
<Features />
<Technologies />
<Faqs />
<Testimonials />
<Metrics />
