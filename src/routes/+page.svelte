<script lang="ts">
	import { asset } from '$app/paths';
	import Section from '$lib/components/section.svelte';
	import Slider from '$lib/components/slider.svelte';
	import Waves from '$lib/components/waves.svelte';
	import { Github, Linkedin, ArrowDown } from 'lucide-svelte';
</script>
<div class="bg-red-900">
	<div class="relative flex min-h-screen min-w-screen bg-amber-50 flex-col p-4">
		<div class="z-10 grow flex flex-col">
			<div class="flex flex-row justify-between">
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
							<h1 class="font-serif text-4xl font-medium">Kevin Faulhaber</h1>
							<span>Senior Software Engineer</span>
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
			<div class="flex flex-col justify-center items-center grow gap-8">
				<div class="flex flex-col justify-center items-center">
					<p class="text-xl">I build things pragmatically.</p>
					<p class="text-xl">Things that work. Things that are tested. Things with best practices in mind.</p>
					<p class="text-xl">I'm honest, straight forward and down to earth.</p>
					<p class="text-xl">I'm a mentor and a leader.</p>
				</div>
				<a href="#about-me" class="animate-bounce">
					<ArrowDown size={42}/>
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
	<section id="about-me" class="mt-24 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4 px-8 [&_*]:text-white">
		<Section
			title="Open Source"
			items={[{
				title: "nuke_modules",
				link: "https://github.com/kemicofa/nuke_modules",
				description: `A CLI built with Rust to find all node_modules starting from the current working directory and delete them.`
			}, {
				title: "Real Time Cartographer",
				link: "https://github.com/kemicofa/rtc",
				description: `A project built in Rust to generate a visualization of a GCP cloud infrastructure by parsing logs and inferring relationships and adding them to a graph database.`
			}, {
				title: "Chockblain",
				link: "https://github.com/kemicofa/chockblain",
				description: "A small blockchain library built with Typescript & Deno"
			}]}
		/>
		<Section
			title={`${new Date().getFullYear() - 2015} years of Experience`}
			items={[{
				title: "Shine.fr",
				link: "https://shine.fr",
				description: `
					An online bank for small businesses simplifying administrative tasks
					so clients can focus on their business.
				`,
				yearRange: {
					start: '2020',
					end: 'present'
				}
			}, {
				title: "Ogury.com",
				link: "https://ogury.com",
				description: `
					Mobile AD company serving 400 milliion devices around the world.	
				`,
				yearRange: {
					start: '2019',
					end: '2020'
				}
			}, {
				title: "Freelance",
				description: `
					Worked closely with IRCAD & IHU on an innovative
					fullstack project to help diagnos the gastic reflux disease
					for two years.
				`,
				yearRange: {
					start: '2017',
					end: '2019'
				}
			}, {
				title: "University Teacher",
				description: `
					Introduction to HTML, CSS and JavaScript @ Robert Schuman Strasbourg.	
					Deep dive into iOS development with Swift & Xcode @ Supinfo Strasbourg.
					Bluetooth communication @ CCI Colmar	
				`,
				yearRange: {
					start: '2018',
					end: '2021'
				}
			}, {
				title: "WeBSurg",
				description: `
					Apprenticeship at the world's largest online university
					for minimally invasive surgery.	
				`,
				link: "https://websurg.com",
				yearRange: {
					start: '2015',
					end: '2017'
				}
			}]}
		/>
		<Section 
			title="Education"
			items={[{
				title: "Master's Degree",
				description: "@ Supinfo",
				link: "https://supinfo.com"
			}, {
				title: "Bachlor's Degree",
				description: "@ University Robert Schuman",
				link: "https://iutrs.unistra.fr"
			}, {
				title: "University of Technology Diplome",
				description: "@ University Robert Schuman",
				link: "https://iutrs.unistra.fr"
			}]}
		/>
	</section>

	<div class="flex justify-center my-24">
		<a rel="noopener noreferrer" target="_blank" href="https://linkedin.com/in/kevin-faulhaber" class="px-4 py-2 rounded cursor bg-black text-white">Hire me</a>
	</div>

	<footer class="[&_*]:text-white flex flex-row justify-center py-4 mt-24">
		<span class="text-center">© {new Date().getFullYear()} Kemicofa Germany </span>
	</footer>
</div>