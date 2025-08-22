<script lang="ts">
	import * as Tooltip from '$lib/components/ui/tooltip/index.js';
	import { Button } from '$lib/components/ui/button';
	import { PartyPopperIcon } from '@lucide/svelte';

	const tech = [
		{
			name: 'Svelte 5',
			image: '/tech/svelte.svg',
			description:
				'The latest generation of Svelte — faster, simpler, and more powerful. With runes, improved reactivity, and a leaner core, Svelte 5 lets you build reactive UIs with less code and better performance.',
			tip: 'Frontend Framework'
		},
		{
			name: 'Auth.js',
			image: '/tech/authjs.webp',
			description:
				'Seamless, secure, and flexible authentication for your app. With support for OAuth, email magic links, and custom providers, Auth.js lets you add login in minutes — no security headaches.',
			tip: 'User Authentication'
		},
		{
			name: 'Drizzle ORM',
			image: '/tech/drizzle.svg',
			description:
				'Type-safe, lightning-fast database access with zero hassle. Drizzle ORM supports PostgreSQL, MySQL, SQLite, and more — making queries reliable, readable, and future-proof.',
			tip: 'Database'
		},
		{
			name: 'Resend',
			image: '/tech/resend.svg',
			darkImage: '/tech/resend-dark.svg',
			description:
				'Send beautiful, reliable emails without the pain. From onboarding flows to password resets, Resend ensures every message lands where it should — in your user’s inbox.',
			tip: 'Sending Emails'
		},
		{
			name: 'Zod',
			image: '/tech/zod.webp',
			description:
				'Never trust unchecked data again. Zod gives you bulletproof schema validation for forms, APIs, and more — so your app stays robust, predictable, and bug-free.',
			tip: 'Schema Validation'
		},
		{
			name: 'Formsnap',
			image: '/tech/formsnap.svg',
			description:
				'Make form handling effortless. Formsnap works hand-in-hand with Zod to validate inputs, display errors instantly, and give users a smooth, frustration-free experience.',
			tip: 'Form Handling'
		},
		{
			name: 'Shadcn-svelte',
			image: '/tech/shadcn-svelte.svg',
			description:
				'Pixel-perfect UI components with accessibility baked in. shadcn-svelte helps you build a stunning interface without reinventing the wheel — all while keeping full control of your code.',
			tip: 'Accessible Components'
		},
		{
			name: 'S3 Compatible Storage',
			image: '/tech/s3.webp',
			description:
				'Store and serve files seamlessly with any S3-compatible storage provider. From AWS S3 to MinIO and DigitalOcean Spaces, it integrates smoothly for uploads, avatars, and media handling.',
			tip: 'File Storage'
		}
	];
</script>

<section class="bg-secondary py-24 px-4" id="technologies-section">
	<div class="container mx-auto gap-8">
		<div class="mx-auto mb-16 max-w-4xl text-center">
			<h2 class="mb-2 text-4xl font-medium text-foreground">
				Powered by Modern, Battle-Tested Tools
			</h2>
			<p class="leading-relaxed text-muted-foreground">
				Every feature in this starter is built with a carefully chosen stack — from authentication
				to database to UI — so you can launch with confidence and scale without limits.
			</p>
		</div>
		<div class="mx-auto my-16 grid gap-8 xl:grid-cols-2">
			{#each tech as { name, image, darkImage, description, tip } (name)}
				<Tooltip.Provider>
					<Tooltip.Root>
						<Tooltip.Trigger>
							{#snippet child({ props })}
								<div
									{...props}
									class="flex flex-row items-start gap-6 rounded-xl bg-background p-6 md:items-center"
									aria-label={name}
									role="button"
									tabindex="0"
								>
									{#if darkImage}
										<img src={image} alt={name} class="mt-4 w-8 md:mt-0 md:w-16 dark:hidden" />
										<img
											src={darkImage}
											alt={name}
											class="mt-4 hidden w-8 md:mt-0 md:w-16 dark:block"
										/>
									{:else}
										<img src={image} alt={name} class="mt-4 w-8 md:mt-0 md:w-16" />
									{/if}
									<div class="flex flex-col gap-2">
										<h3 class="text-lg font-medium">{name}</h3>
										<p class="leading-relaxed text-muted-foreground">{description}</p>
									</div>
								</div>
							{/snippet}
						</Tooltip.Trigger>
						<Tooltip.Content>
							<p>{tip}</p>
						</Tooltip.Content>
					</Tooltip.Root>
				</Tooltip.Provider>
			{/each}
		</div>
		<div class="mt-4 flex items-center justify-center gap-2">
			<Button href="https://component.directory/sveltekit-starter" title="Get Access">
				<PartyPopperIcon />
				Check out full version
			</Button>
		</div>
	</div>
</section>
