<script lang="ts">
	import { DatabaseIcon, LayoutIcon, ListTodoIcon, UserCheckIcon } from '@lucide/svelte';
	import { Separator } from '$lib/components/ui/separator';

	const features = [
		{
			title: 'Authentication Ready',
			description: 'Sign up, login, and secure sessions — done.',
			icon: UserCheckIcon
		},
		{
			title: 'Database Integrated',
			description: 'Models, migrations, and queries included out of the box.',
			icon: DatabaseIcon
		},
		{
			title: 'Production-Ready Scaffold',
			description: 'Start with a clean app structure designed for growth.',
			icon: LayoutIcon
		},
		{
			title: 'Example App Included',
			description:
				'Jump straight into a working Task Manager demo. Replace “To-Dos” with your own data model — customers, posts, notes, or anything else.',
			icon: ListTodoIcon
		}
	];
</script>

<section class="py-24 px-4">
	<div class="mx-auto mb-16 max-w-4xl text-center">
		<h2 class="mb-2 text-4xl font-medium text-foreground">Everything You Need to Launch Faster</h2>
		<p class="leading-relaxed text-muted-foreground">
			Skip boilerplate and focus on what makes your product unique.
		</p>
	</div>
	<div class="container mx-auto grid grid-cols-1 items-start gap-8 md:grid-cols-2 xl:grid-cols-4">
		{#each features as { title, description, icon: Icon }, i (i)}
			<div class="relative cursor-default rounded-xl p-8 max-md:text-center">
				<Icon class="mb-8 size-12 text-muted-foreground max-md:mx-auto" />
				<h3 class="mb-2 text-lg leading-none font-medium text-foreground">{title}</h3>
				<p class="leading-relaxed text-muted-foreground">{description}</p>
				{#if i !== features.length - 1}
					<Separator
						orientation="vertical"
						class={`absolute top-1/2 -right-px !h-16 -translate-y-1/2 ${i === 1 ? 'max-xl:hidden' : 'max-md:hidden'}`}
					/>
				{/if}
			</div>
		{/each}
	</div>
</section>
