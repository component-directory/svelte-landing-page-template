<script>
	import { Badge } from '$lib/components/ui/badge';
	import { Button } from '$lib/components/ui/button';
	import { ArrowRightIcon } from '@lucide/svelte';
	import { Label } from '../ui/label';
	import { Switch } from '../ui/switch';
	import { cn } from '$lib/utils';

	let useSveltekitStarter = $state(false);

	const partners = [
		{
			logoSrc: '/partners/logo-1.svg',
			darkLogoSrc: '/partners/logo-1-dark.svg',
			href: '##'
		},
		{
			logoSrc: '/partners/logo-2.svg',
			darkLogoSrc: '/partners/logo-2-dark.svg',
			href: '##'
		},
		{
			logoSrc: '/partners/logo-3.svg',
			darkLogoSrc: '/partners/logo-3-dark.svg',
			href: '##'
		},
		{
			logoSrc: '/partners/logo-4.svg',
			darkLogoSrc: '/partners/logo-4-dark.svg',
			href: '##'
		},
		{
			logoSrc: '/partners/logo-5.svg',
			darkLogoSrc: '/partners/logo-5-dark.svg',
			href: '##'
		}
	];
</script>

<section
	id="hero-section"
	class="container mx-auto grid min-h-dvh items-center justify-center gap-8 px-4 py-8 xl:grid-cols-2"
>
	<div class="flex flex-col items-start">
		<Badge variant={'secondary'} class="mb-2">Beta</Badge>
		<h1 class="mb-4 text-5xl font-black text-foreground">Build SaaS Faster, Smarter</h1>
		<p class="mb-8 leading-relaxed text-muted-foreground">
			Skip the setup. Get authentication, database, and a clean scaffold already wired up. Focus on
			your product, not boilerplate.
		</p>
		<Button href="https://component.directory/sveltekit-starter" size="lg"
			>Get Lifetime Access <ArrowRightIcon /></Button
		>
		<div class="mt-16 overflow-hidden rounded-2xl bg-secondary p-4">
			<div class="grid grid-cols-3 items-center justify-between gap-4 md:grid-cols-5">
				{#each partners as { logoSrc, darkLogoSrc, href }, i (i)}
					<a
						href={href ?? '##'}
						class="p-4 opacity-50 transition hover:opacity-100"
						class:hidden={i > 2}
						class:md:block={i > 2}
					>
						<img src={logoSrc} alt="View Partner {i + 1}" class="dark:hidden" />
						<img src={darkLogoSrc} alt="View Partner {i + 1}" class="hidden dark:block" />
					</a>
				{/each}
			</div>
		</div>
	</div>
	<div class="relative hidden flex-col items-center justify-center gap-4 xl:flex">
		<div class="flex flex-col items-center justify-center gap-2">
			<div class:hidden={useSveltekitStarter}>
				<img
					src="/before.jpg"
					alt="Hero"
					class="mx-auto rounded-lg border-4 border-[#feecd1] dark:hidden"
				/>
				<img
					src="/before-dark.jpg"
					alt="Hero"
					class="mx-auto hidden rounded-lg border-4 border-[#feecd1cc] dark:block"
				/>
			</div>
			<div class="hidden" class:!block={useSveltekitStarter}>
				<img
					src="/after.jpg"
					alt="Hero"
					class="mx-auto rounded-lg border-4 border-[#feecd1] dark:hidden"
				/>
				<img
					src="/after-dark.jpg"
					alt="Hero"
					class="mx-auto hidden rounded-lg border-4 border-[#feecd1cc] dark:block"
				/>
			</div>
			<Label
				class={cn(
					'cursor-pointer rounded-lg bg-secondary p-2 text-xs transition hover:text-secondary-foreground',
					useSveltekitStarter ? 'text-secondary-foreground' : 'text-muted-foreground'
				)}
			>
				<Switch bind:checked={useSveltekitStarter} />
				Use Sveltekit Starter?
			</Label>
		</div>
	</div>
</section>
