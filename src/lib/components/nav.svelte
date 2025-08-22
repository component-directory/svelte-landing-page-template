<script lang="ts">
	import * as NavigationMenu from '$lib/components/ui/navigation-menu/index.js';
	import * as Sheet from '$lib/components/ui/sheet/index.js';
	import { navigationMenuTriggerStyle } from '$lib/components/ui/navigation-menu/navigation-menu-trigger.svelte';
	import { buttonVariants } from '$lib/components/ui/button/button.svelte';
	import { MenuIcon } from '@lucide/svelte';
	import { cn } from '$lib/utils';
	const navItems: {
		title: string;
		href: string;
		// below fields used for scrolling to section on click
		sectionId?: string;
		onclick?: () => void;
	}[] = [
		{
			title: 'Getting Started',
			href: '##',
			sectionId: 'hero-section',
			onclick: () => {
				scrollToSection('hero-section');
			}
		},
		{
			title: 'Tech',
			href: '##',
			sectionId: 'technologies-section',
			onclick: () => {
				scrollToSection('technologies-section');
			}
		},
		{
			title: 'FAQs',
			href: '##',
			sectionId: 'faqs-section',
			onclick: () => {
				scrollToSection('faqs-section');
			}
		}
	];

	let activeSection = $state<string>('hero-section');

	function scrollToSection(sectionId: string) {
		const section = document.getElementById(sectionId);
		if (section) {
			section.scrollIntoView({ behavior: 'smooth' });
		}
	}

	$effect(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				for (const entry of entries) {
					if (entry.isIntersecting) {
						activeSection = entry.target.id;
					}
				}
			},
			{
				threshold: 0.5
			}
		);

		navItems.forEach((item) => {
			if (!item.sectionId) return;
			const el = document.getElementById(item.sectionId);
			if (el) observer.observe(el);
		});

		return () => observer.disconnect();
	});

	let mobileMenuOpen = $state<boolean>(false);
</script>

<NavigationMenu.Root viewport={false} class="hidden lg:block">
	<NavigationMenu.List>
		{#each navItems as { title, href, sectionId, onclick }, i (i)}
			<NavigationMenu.Item>
				<NavigationMenu.Link active={activeSection === sectionId}>
					{#snippet child({ props })}
						<a
							{...props}
							{href}
							onclick={(e) => {
								if (!onclick) return;
								e.preventDefault();
								onclick();
							}}
							class={navigationMenuTriggerStyle({
								class: 'bg-transparent not-[[data-active]]:!bg-transparent data-active:bg-secondary'
							})}>{title}</a
						>
					{/snippet}
				</NavigationMenu.Link>
			</NavigationMenu.Item>
		{/each}
	</NavigationMenu.List>
</NavigationMenu.Root>

<Sheet.Root bind:open={mobileMenuOpen}>
	<Sheet.Trigger
		class={buttonVariants({ variant: 'outline', size: 'icon', class: 'mr-auto lg:hidden' })}
	>
		<MenuIcon />
	</Sheet.Trigger>
	<Sheet.Content side="right" class="overflow-y-scroll" preventScroll={false}>
		<div class="mt-8 flex flex-col gap-1 p-4">
			{#each navItems as { title, href, sectionId, onclick }, i (i)}
				<a
					{href}
					onclick={(e) => {
						if (!onclick) return;
						e.preventDefault();
						mobileMenuOpen = false;
						setTimeout(() => {
							onclick();
						}, 500);
					}}
					class={cn(
						navigationMenuTriggerStyle({
							class: 'w-full justify-start !bg-transparent'
						})
					)}
					class:!bg-secondary={activeSection === sectionId}>{title}</a
				>
			{/each}
		</div>
	</Sheet.Content>
</Sheet.Root>
