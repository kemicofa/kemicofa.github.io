<script lang="ts">
	import { asset } from '$app/paths';
	import Waves from '$lib/components/waves.svelte';
	import { Github, Linkedin } from 'lucide-svelte';
</script>

<div class="relative flex min-h-screen min-w-screen flex-col">
	<div class="z-10 flex flex-col">
		<div class="mt-12 flex flex-col items-center justify-center gap-8 md:flex-row">
			<div
				class="relative flex h-64 w-64 justify-center before:absolute before:inset-0 before:animate-[pulse_6s_ease-in-out_infinite] before:rounded-full before:bg-amber-100"
			>
				<figure class="flex flex-col justify-center">
					<img
						class="relative z-10 w-48 rounded-full"
						alt="Profile of Kevin Faulhaber"
						src={asset('/kemicofa.jpg')}
					/>
				</figure>
			</div>

			<div class="flex flex-col items-center gap-2">
				<h1 class="font-serif text-4xl font-medium">Kevin Faulhaber</h1>
				<span>Senior Software Engineer</span>
				<aside class="flex justify-end gap-4 px-4 py-2">
					<a href="https://github.com/kemicofa" target="_blank" rel="noopener noreferrer">
						<Github class="h-6 w-6 text-gray-700 hover:text-blue-600" />
					</a>
					<a
						href="https://linkedin.com/in/kevin-faulhaber"
						target="_blank"
						rel="noopener noreferrer"
					>
						<Linkedin class="h-6 w-6 text-gray-700 hover:text-blue-600" />
					</a>
				</aside>
			</div>
		</div>
	</div>

	<div class="absolute top-0 left-0">
		<Waves class="max-h-screen min-h-screen max-w-screen min-w-screen" />
	</div>
</div>
