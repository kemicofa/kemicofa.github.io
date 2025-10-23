<script lang="ts">
	import { asset } from '$app/paths';
	import { HelpCircleIcon, Target } from 'lucide-svelte';
	import Tech from './tech.svelte';

	const nowYear = new Date().getFullYear();

	const technologies = [
		{
			src: '/icons/nodejs.svg',
			title: 'Node.js',
			expYears: nowYear - 2015,
			abstract: `I enjoy the Node.js ecosystem — a single-threaded event loop that efficiently delegates work to multiple threads, making it non-blocking and highly scalable.`,
			experiences: [
				'At Shine.fr, contributed to and created internal libraries, monorepos, and microservices written in Node.js.',
				'At Ogury.com, worked on both client-side libraries and backend microservices using Node.js.',
				'As a freelancer, built a React Native application for doctors.',
				'At WebSurg, wrote my first client-side TypeScript project within the Node.js ecosystem.'
			]
		},
		{
			src: '/icons/typescript.svg',
			title: 'TypeScript',
			expYears: nowYear - 2015,
			abstract:
				'I have used TypeScript in every role I’ve held. It’s my daily driver and an essential tool for type safety and maintainability in JavaScript projects.',
			experiences: [
				'At Shine.fr, built React, React Native, and backend services in TypeScript. Converted multiple microservices from plain JavaScript to progressively typed codebases.',
				'At Ogury.com, contributed to user-facing React applications written in TypeScript.',
				'As a freelancer, used TypeScript with React Native to build an app for doctors.',
				'At WebSurg, introduced TypeScript for a client-side app and integrated it with a PHP/Symfony backend.'
			]
		},
		{
			src: '/icons/rust.svg',
			title: 'Rust',
			expYears: nowYear - 2020,
			abstract:
				'Rust is my favorite language for systems programming. I’ve used it in side and open-source projects and am comfortable with the borrow checker, async/await, and lifetimes.',
			experiences: [
				'"nuke_modules" — an open-source Rust CLI that locates and deletes all node_modules directories for faster disk cleanup.',
				'"Real Time Cartographer" — an open-source project that ingests GCP logs and builds a dependency graph of microservices and their endpoints.'
			]
		},
		{
			src: '/icons/svelte.svg',
			title: 'Svelte',
			expYears: nowYear - 2021,
			abstract:
				'Inspired by Rich Harris’s “Rethinking Reactivity” talk, I believe frameworks like Svelte represent the future of web development — simpler, faster, and more intuitive than React’s model.',
			experiences: [
				'Built my personal website (kemicofa.github.io) using SvelteKit.',
				'Developing a car rental website for a Swiss client using SvelteKit, Flowbite, and Tailwind CSS.'
			]
		},
		{
			src: '/icons/tailwindcss.svg',
			title: 'Tailwind CSS',
			expYears: nowYear - 2021,
			abstract:
				'A utility-first CSS framework I use regularly for building modern and responsive UIs.',
			experiences: [
				'Developing a Swiss car rental website with SvelteKit, Flowbite, and Tailwind CSS.',
				'Built my personal site (kemicofa.github.io) with Tailwind CSS.'
			]
		},
		{
			src: '/icons/docker.svg',
			title: 'Docker',
			expYears: nowYear - 2017,
			abstract:
				'I use Docker extensively for local development, CI/CD testing, and deployment across multiple environments.',
			experiences: [
				'At Shine.fr, used for local development, CI/CD pipelines, and deployments to GCP Cloud Run and Cloud Functions.',
				'At Ogury.com, used for local development and deployments to AWS.',
				'As a freelancer, containerized a full-stack app for deployment on IRCAD & IHU internal servers.'
			]
		},
		{
			src: '/icons/apollographql.svg',
			title: 'Apollo GraphQL',
			expYears: nowYear - 2020,
			abstract:
				'A powerful abstraction over HTTP that makes querying backend data intuitive. I’ve used Apollo to design robust and developer-friendly APIs.',
			experiences: [
				'At Shine.fr, refactored and converted the GraphQL codebase to TypeScript, restructured queries/mutations, and used Apollo Client in React and React Native apps.'
			]
		},
		{
			src: '/icons/bun.svg',
			title: 'Bun',
			expYears: nowYear - 2022,
			abstract:
				'I started using Bun early on as a fast and simple alternative to Node.js and Deno for TypeScript projects. It’s great for CLIs and developer tooling.',
			experiences: [
				'At Shine.fr, presented Bun to the engineering team and led its adoption for internal CLI tooling. Built a diagnostic CLI for financial synchronization issues, now used regularly across teams.'
			]
		},
		{
			src: '/icons/deno.svg',
			title: 'Deno',
			expYears: nowYear - 2021,
			abstract:
				'Deno is my go-to for lightweight projects that don’t require the NPM ecosystem. I appreciate its security model and built-in tooling.',
			experiences: [
				'At Shine.fr, presented a talk on Deno and its origins by Ryan Dahl.',
				'"Chockblain" — a small open-source blockchain library written in Deno.'
			]
		},
		{
			src: '/icons/mongodb.svg',
			title: 'MongoDB',
			expYears: nowYear - 2018,
			abstract:
				'I enjoy using MongoDB for smaller projects, especially for its flexible schema and aggregation capabilities.',
			experiences: [
				'NovaLux.io — a discontinued startup aiming to reinvent how we read Light Novels.',
				'Yotee.co — a discontinued startup aiming to modernize the yachting industry.'
			]
		},
		{
			src: '/icons/neo4j.svg',
			title: 'FalkorDB',
			expYears: nowYear - 2025,
			abstract:
				'Graph databases and the Cypher query language make data relationships intuitive and powerful.',
			experiences: [
				'"Real Time Cartographer" — a Rust project that parses GCP logs, builds dependency graphs, and stores them in FalkorDB.'
			]
		},
		{
			src: '/icons/postgresql.svg',
			title: 'PostgreSQL',
			expYears: nowYear - 2021,
			abstract:
				'A robust, feature-rich SQL database. One of my go-to tools for production-grade applications.',
			experiences: [
				'At Shine.fr, implemented a partitioned and indexed PostgreSQL database to handle high-frequency data ingestion and used WAL CDC for asynchronous log forwarding.',
				'Yotee.co used PostgreSQL for parts of its application backend.'
			]
		},
		{
			src: '/icons/react.svg',
			title: 'React',
			expYears: nowYear - 2017,
			abstract:
				'The first frontend framework I truly loved. React reshaped how I think about building user interfaces.',
			experiences: [
				'At Shine.fr, contributed extensively to React web apps, React Native mobile apps, and internal backoffice tools using TanStack and Apollo Client.',
				'At Ogury.com, used React to build innovative ad formats for millions of users.',
				'As a freelancer, built a React Native app to help diagnose gastric reflux disease.'
			]
		},
		{
			src: '/icons/redis.svg',
			title: 'Redis',
			expYears: nowYear - 2019,
			abstract: 'My go-to tool for caching, real-time data, and pub/sub messaging systems.',
			experiences: [
				'At Shine.fr, used Redis for caching and pub/sub mechanisms.',
				'At Ogury.com, used Redis primarily for caching.'
			]
		},
		{
			src: '/icons/terraform.svg',
			title: 'Terraform',
			expYears: nowYear - 2023,
			abstract:
				'A great tool for managing infrastructure as code. I’ve used it to define cloud services and automate deployments.',
			experiences: [
				'At Shine.fr, used Terraform to define account services and deploy GCP resources (Cloud Run, Cloud Functions, Pub/Sub, scheduled jobs).'
			]
		}
	] satisfies {
		src: string;
		title: string;
		expYears: number;
		experiences: string[];
		abstract: string;
	}[];

	type Tech = (typeof technologies)[number];

	interface Modal {
		open: boolean;
		sticky: boolean;
		target?: Tech;
	}
	let modal = $state<Modal>({
		open: false,
		sticky: false,
		target: undefined
	});
</script>

<div class="relative w-full">
	<div
		class:animate-fade-in={modal.open}
		class:animate-fade-out={!modal.open}
		id="slider-modal"
		class="absolute bottom-40 flex w-full justify-center px-8"
	>
		<div
			class="flex flex-col items-center justify-center rounded border border-white p-4 md:max-w-3/5 md:min-w-2/5 xl:min-w-1/4 [&_*]:text-white"
		>
			{#if modal.target}
				<Tech
					experiences={modal.target.experiences}
					title={modal.target.title}
					expYears={modal.target.expYears}
					abstract={modal.target.abstract}
				/>
			{:else}
				<p>Oops something went wrong.</p>
			{/if}
		</div>
	</div>
	<div class="relative w-full overflow-hidden py-6">
		<div class="animate-slide flex w-max items-center will-change-transform">
			<!-- Duplicate the icon list to create seamless looping -->
			{#each [...technologies, ...technologies] as tech, i (tech.src + Math.random())}
				<button
					class="flex cursor-pointer flex-col items-center justify-center"
					onclick={() => {
						modal.open = true;
						modal.sticky = true;
						modal.target = tech;
					}}
					onblur={() => {
						modal.open = false;
						modal.sticky = false;
					}}
					onmouseenter={() => {
						if (modal.sticky) {
							return;
						}
						modal.open = true;
						modal.target = tech;
					}}
					onmouseleave={() => {
						if (modal.sticky) {
							return;
						}
						modal.open = false;
					}}
				>
					<img
						aria-hidden={i > technologies.length - 1}
						src={asset(tech.src)}
						alt={tech.title}
						class="mx-6 h-12 w-12 opacity-70 transition-opacity hover:animate-wiggle hover:opacity-100"
					/>
					<span class="text-sm">{tech.title}</span>
				</button>
			{/each}
		</div>
	</div>
</div>

<style global>
	@keyframes slide {
		0% {
			transform: translateX(0);
		}
		100% {
			transform: translateX(-50%);
		}
	}

	@keyframes fade-in {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}

	@keyframes fade-out {
		from {
			opacity: 1;
		}
		to {
			opacity: 0;
		}
	}

	.animate-fade-in {
		animation: fade-in 1s ease forwards;
	}

	.animate-fade-out {
		animation: fade-out 0.5s ease forwards;
	}

	.animate-slide {
		animation: slide 20s linear infinite;
	}

	.animate-slide:hover {
		animation-play-state: paused;
	}
</style>
