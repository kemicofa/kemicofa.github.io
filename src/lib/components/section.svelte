<script lang="ts">
	import Link from './link.svelte';

	interface SectionProps {
		class?: string;
		title: string;
		items: {
			title: string;
			description?: string;
			link?: string;
			yearRange?: {
				start: string;
				end?: string;
			};
		}[];
	}

	let { class: outerClass, title, items }: SectionProps = $props();
</script>

{#snippet subheading(item: { link?: string; title: string })}
	<h4 class="text-xl">
		{#if item.link}
			<Link href={item.link} text={item.title} />
		{:else}
			{item.title}
		{/if}
	</h4>
{/snippet}

<div class={`${outerClass} flex flex-col gap-12`}>
	<h2 class="text-center font-serif text-3xl font-medium">{title}</h2>
	<div class="flex flex-col gap-8">
		{#each items as item}
			<div class="flex flex-col gap-2">
				{#if item.yearRange}
					<div class="flex flex-row items-baseline justify-between">
						{@render subheading(item)}
						<span class="text-nowrap"
							>{item.yearRange.start}{item.yearRange.end ? ` - ${item.yearRange.end}` : ''}</span
						>
					</div>
				{:else}
					{@render subheading(item)}
				{/if}
				{#if item.description}
					<p>
						{item.description}
					</p>
				{/if}
			</div>
		{/each}
	</div>
</div>
