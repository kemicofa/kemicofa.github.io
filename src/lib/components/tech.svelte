<script lang="ts">
	interface Tech {
		title: string;
		expYears: number;
		abstract: string;
		experiences: string[];
	}

	let { title, expYears, experiences, abstract }: Tech = $props();
</script>

<div class="flex w-full flex-col gap-4 [&_*]:text-white">
	<div class="flex flex-row items-baseline justify-between">
		<h5 class="font-serif text-xl font-medium">{title}</h5>
		<span>{Math.max(expYears, 1)} year{expYears > 1 ? 's' : ''} of experience</span>
	</div>
	<div class="flex flex-col gap-1">
		<span class="font-serif">Abstract:</span>
		<p>{abstract}</p>
	</div>
	<div class="flex flex-col gap-1">
		<span class="font-serif">Experiences:</span>
		<ul class="ml-6 flex list-disc flex-col gap-1">
			{#each experiences as e}
				<li>{e}</li>
			{/each}
		</ul>
	</div>
</div>
