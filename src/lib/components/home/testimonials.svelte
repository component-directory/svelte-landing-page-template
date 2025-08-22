<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { PartyPopperIcon } from '@lucide/svelte';

	const testimonials = [
		{
			name: 'Sarah K.',
			role: 'Full-stack Developer',
			quote:
				'This starter kit saved me weeks of setup. Everything from authentication to database was ready to go, and I launched my MVP in days instead of months.'
		},
		{
			name: 'David R.',
			role: 'Indie Hacker',
			quote:
				'I’ve bought a lot of templates before, but this one feels like it was made for speed and practicality. The code quality is excellent and easy to extend.'
		},
		{
			name: 'Leila A.',
			role: 'Startup Founder',
			quote:
				'The built-in authentication and database layer meant I could focus on my core product, not boilerplate. Absolutely worth the price.'
		},
		{
			name: 'Jonas P.',
			role: 'Freelance Engineer',
			quote:
				'Clients love how fast I can deliver. This kit gave me a solid foundation I can reuse across multiple projects.'
		},
		{
			name: 'Marta S.',
			role: 'Product Designer & Developer',
			quote:
				'It’s more than a starter — it feels like a best-practice blueprint. Perfect balance of features and simplicity.'
		},
		{
			name: 'Alex W.',
			role: 'Tech Entrepreneur',
			quote:
				'I was skeptical at first, but this kit paid for itself within the first week. It’s like having a senior engineer set up the boring parts for you.'
		}
	];
</script>

<section class="bg-secondary py-24 px-4">
	<div class="mx-auto mb-16 max-w-4xl text-center">
		<h2 class="mb-2 text-4xl font-medium text-foreground">What Developers Are Saying</h2>
		<p class="leading-relaxed text-muted-foreground">
			Trusted by professionals who ship faster with our starter kit
		</p>
	</div>

	<div class="container mx-auto">
		<div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
			{#each testimonials as testimonial, i (i)}
				<div class="rounded-xl bg-card dark:bg-accent/30 p-6 text-card-foreground">
					<p class="mb-4 text-muted-foreground">"{testimonial.quote}"</p>
					<div>
						<p class="font-semibold text-foreground">{testimonial.name}</p>
						<p class="text-sm text-muted-foreground">{testimonial.role}</p>
					</div>
				</div>
			{/each}
		</div>
		<div class="mt-24 flex items-center justify-center">
			<Button href="https://component.directory/sveltekit-starter" title="Get Access">
				<PartyPopperIcon />
				Get Lifetime Access
			</Button>
		</div>
	</div>
</section>
