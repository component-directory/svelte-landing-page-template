<script lang="ts">
	import * as Accordion from '$lib/components/ui/accordion/index.js';
	import { cn } from '$lib/utils';
	const faqs = [
		{
			question: 'What exactly does this starter kit include?',
			answer:
				'It includes a complete foundation with authentication, database integration, error handling, UI components, and a production-ready setup — everything you need to start building fast.'
		},
		{
			question: 'Who is this starter kit for?',
			answer:
				'It’s built for indie hackers, startup founders, freelancers, and developers who want to save time and focus on their product rather than boilerplate setup.'
		},
		{
			question: 'Do I get lifetime access?',
			answer: 'Yes. Once you purchase, you have lifetime access to the codebase and future updates.'
		},
		{
			question: 'Can I use this for client projects?',
			answer:
				'Absolutely. You can use it for personal or commercial projects, including client work.'
		},
		{
			question: 'How do I pay for the starter kit?',
			answer: 'Currently, payment is accepted exclusively via cryptocurrency.'
		},
		{
			question: 'Is it production ready?',
			answer:
				'Yes, it follows modern best practices and is designed for real-world production use. Many users have launched live products directly from it.'
		}
	];
</script>

<section id="faqs-section" class="py-24 px-4">
	<div class="mx-auto mb-16 max-w-4xl text-center">
		<h2 class="mb-2 text-4xl font-medium text-foreground">Frequently Asked Questions</h2>
		<p class="leading-relaxed text-muted-foreground">
			Everything you need to know before getting started
		</p>
	</div>
	<div class="container mx-auto">
		<Accordion.Root type="single" class="mx-auto w-full sm:max-w-[70%]" value="0">
			{#each faqs as { question, answer }, i (i)}
				<Accordion.Item value={String(i)}>
					<Accordion.Trigger
						class={cn(
							'h-[unset] cursor-pointer p-6 text-base text-foreground hover:bg-secondary hover:no-underline data-[state=open]:bg-secondary',
							i > 0 && 'rounded-none',
							i === 0 && 'rounded-t-lg rounded-b-none',
							i === faqs.length - 1 && 'data-[state=closed]:rounded-b-lg'
						)}>{question}</Accordion.Trigger
					>
					<Accordion.Content class="flex flex-col gap-4 p-4 pb-8 text-base leading-relaxed">
						<p>{answer}</p>
					</Accordion.Content>
				</Accordion.Item>
			{/each}
		</Accordion.Root>
	</div>
</section>
