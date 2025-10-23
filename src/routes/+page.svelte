<script lang="ts">
	import { asset } from '$app/paths';
	import Section from '$lib/components/section.svelte';
	import Slider from '$lib/components/slider.svelte';
	import Waves from '$lib/components/waves.svelte';
	import { Github, Linkedin, ArrowDown } from 'lucide-svelte';
</script>

<div class="bg-red-900">
	<div class="relative flex min-h-screen min-w-screen flex-col bg-amber-50 p-4">
		<div class="z-10 flex grow flex-col">
			<div class="flex flex-col items-center justify-between md:flex-row">
				<div class="flex flex-col">
					<div class="flex flex-col items-center gap-8 md:flex-row">
						<div
							class="relative flex h-32 w-32 justify-center before:absolute before:inset-0 before:animate-[pulse_6s_ease-in-out_infinite] before:rounded-full before:bg-amber-100"
						>
							<figure class="flex flex-col justify-center">
								<img
									class="relative z-10 w-24 rounded-full"
									alt="Profile of Kevin Faulhaber"
									src={asset('/kemicofa.jpg')}
								/>
							</figure>
						</div>

						<div class="flex flex-col gap-1">
							<h1 class="font-serif text-4xl font-medium sm:text-center">Kevin Faulhaber</h1>
							<span class="text-center md:text-left">Senior Software Engineer</span>
						</div>
					</div>
				</div>
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
			<div class="flex grow flex-col items-center justify-center gap-16">
				<div class="flex flex-col items-center justify-center gap-1 [&_*]:text-center">
					<p class="text-xl">I build things pragmatically.</p>
					<p class="font-serif text-2xl font-medium">
						Things that work. Things that are tested. Things with best practices in mind.
					</p>
				</div>
				<div class="flex flex-col items-center justify-center gap-1 [&_*]:text-center">
					<p class="text-xl">I'm honest, straight forward and down to earth.</p>
					<p class="text-xl">If I don't know something, tomorrow I'll know.</p>
					<p class="text-xl">I'm a mentor and a leader.</p>
				</div>
				<a href="#about-me" class="animate-bounce rounded-full border-2">
					<ArrowDown size={42} />
				</a>
			</div>
			<div class="grow"></div>
		</div>

		<div class="absolute top-0 left-0">
			<Waves class="max-h-screen min-h-screen max-w-screen min-w-screen" />
		</div>
	</div>

	<div class="h-64 bg-linear-to-b from-warm-red to-red-900"></div>
	<Slider />
	<section
		id="about-me"
		class="mt-24 grid grid-cols-1 gap-4 px-8 sm:grid-cols-2 md:grid-cols-3 [&_*]:text-white"
	>
		<Section
			title="Open Source"
			items={[
				{
					title: 'nuke_modules',
					link: 'https://github.com/kemicofa/nuke_modules',
					description: `A CLI built with Rust to find all node_modules starting from the current working directory and delete them.`
				},
				{
					title: 'Real Time Cartographer',
					link: 'https://github.com/kemicofa/rtc',
					description: `A project built in Rust to generate a visualization of a GCP cloud infrastructure by parsing logs and inferring relationships and adding them to a graph database.`
				},
				{
					title: 'Chockblain',
					link: 'https://github.com/kemicofa/chockblain',
					description: 'A small blockchain library built with Typescript & Deno'
				}
			]}
		/>
		<Section
			title={`${new Date().getFullYear() - 2015} years of Experience`}
			items={[
				{
					title: 'Shine.fr',
					link: 'https://shine.fr',
					description: `
					A leading French online bank supporting small businesses by
					automating administrative processes and simplifying financial management.	
				`,
					yearRange: {
						start: '2020',
						end: 'present'
					}
				},
				{
					title: 'Ogury.com',
					link: 'https://ogury.com',
					description: `
					A global mobile ad tech company serving over 400 million devices worldwide.	
				`,
					yearRange: {
						start: '2019',
						end: '2020'
					}
				},
				{
					title: 'Freelance',
					description: `
					Worked closely with IRCAD and IHU over a two-year period on an innovative full-stack project aimed at helping diagnose gastroesophageal reflux disease (GERD).
				`,
					yearRange: {
						start: '2017',
						end: '2019'
					}
				},
				{
					title: 'University Teacher',
					description: `
					Robert Schuman, Strasbourg — Introduction to HTML, CSS, and JavaScript.
					Supinfo, Strasbourg — Deep dive into iOS development with Swift and Xcode.
					CCI, Colmar — Bluetooth communication fundamentals.
				`,
					yearRange: {
						start: '2018',
						end: '2021'
					}
				},
				{
					title: 'WeBSurg',
					description: `
					Apprenticeship at the world's largest online university
					for minimally invasive surgery.	
				`,
					link: 'https://websurg.com',
					yearRange: {
						start: '2015',
						end: '2017'
					}
				}
			]}
		/>
		<Section
			title="Education"
			items={[
				{
					title: "Master's Degree",
					description: '@ Supinfo',
					link: 'https://supinfo.com',
					yearRange: {
						start: '2015',
						end: '2017'
					}
				},
				{
					title: "Bachlor's Degree",
					description: '@ University Robert Schuman',
					link: 'https://iutrs.unistra.fr',
					yearRange: {
						start: '2014',
						end: '2015'
					}
				},
				{
					title: 'University of Technology Diplome',
					description: '@ University Robert Schuman',
					link: 'https://iutrs.unistra.fr',
					yearRange: {
						start: '2012',
						end: '2014'
					}
				}
			]}
		/>
	</section>

	<div class="my-24 flex justify-center">
		<a
			rel="noopener noreferrer"
			target="_blank"
			href="https://linkedin.com/in/kevin-faulhaber"
			class="cursor rounded bg-black px-4 py-2 text-white">Hire me</a
		>
	</div>

	<footer class="mt-24 flex flex-row justify-center py-4 [&_*]:text-white">
		<span class="text-center">© {new Date().getFullYear()} Kemicofa Germany </span>
	</footer>
</div>
