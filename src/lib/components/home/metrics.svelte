<script>
	import { Button } from '$lib/components/ui/button';
	import { Separator } from '$lib/components/ui/separator';

	const metrics = [
		{
			label: 'Integrations',
			value: '40+'
		},
		{
			label: 'Happy customers',
			value: '21K+'
		},
		{
			label: 'Messages per minute',
			value: '7.3M+'
		},
		{
			label: 'Monthly active users',
			value: '1.5M+'
		}
	];
</script>

<section class="py-24">
	<div class="container mx-auto gap-8 px-4">
		<div class="grid grid-cols-1 xl:grid-cols-3 items-center gap-4">
			<div class="xl:col-span-2 items-center grid sm:grid-cols-2 2xl:grid-cols-4">
				{#each metrics as { label, value }, i (i)}
					<div class="relative flex flex-col items-center gap-4 p-8 text-center">
						<span class="text-6xl font-bold text-secondary-foreground">{value}</span>
						<span class="text-muted-foreground">{label}</span>
						{#if i !== metrics.length - 1}
							<Separator
								orientation="vertical"
								class="absolute top-1/2 right-0 hidden !h-16 -translate-y-1/2 2xl:block"
							/>
						{/if}
					</div>
				{/each}
			</div>
			<div class="flex flex-grow flex-col gap-4">
				<div
					class="flex-grow rounded-xl p-4 leading-relaxed font-light text-foreground bg-secondary"
				>
					<p>
						Use our API to build your own payments experience. We offer a wide range of integrations
						including Stripe, PayPal, and more.
					</p>
				</div>
				<Button variant="default" href="#">Login to See Demo</Button>
			</div>
		</div>
	</div>
</section>