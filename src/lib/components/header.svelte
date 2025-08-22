<script>
	import Nav from '$lib/components/nav.svelte';
	import { Button } from '$lib/components/ui/button/index.js';
	import ThemeToggle from '$lib/components/theme-toggle.svelte';
</script>

<header
	class="sticky top-0 z-50 bg-background/80 backdrop-blur supports-[backdrop-filter]:bg-background/60"
>
	<div class="container mx-auto flex items-center justify-between p-4 gap-4">
		<a href="/" title="Home Page">
			<img src="/logo.svg" alt="Logo" class="dark:hidden" />
			<img src="/logo-dark.svg" alt="Logo" class="hidden dark:block" />
		</a>
		<Nav />
		<div class="flex items-center gap-2">
			<ThemeToggle />
			<Button href="#" variant="default">Login</Button>
		</div>
	</div>
</header>
