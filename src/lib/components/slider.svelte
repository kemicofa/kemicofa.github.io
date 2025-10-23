<script lang="ts">
	import { asset } from "$app/paths";

  const icons = [
    { src: "/icons/nodejs.svg", alt: "Node.js" },
    { src: "/icons/typescript.svg", alt: "TypeScript" },
    { src: "/icons/rust.svg", alt: "Rust" },
    { src: "/icons/svelte.svg", alt: "Svelte" },
    { src: "/icons/tailwindcss.svg", alt: "Tailwind CSS" },
    { src: "/icons/docker.svg", alt: "Docker" },
    { src: "/icons/apollographql.svg", alt: "ApolloGraphql" },
    { src: "/icons/bun.svg", alt: "Bun" },
    { src: "/icons/deno.svg", alt: "Deno" },
    { src: "/icons/kubernetes.svg", alt: "Kubernetes" },
    { src: "/icons/mongodb.svg", alt: "MongoDB" },
    { src: "/icons/neo4j.svg", alt: "neo4j" },
    { src: "/icons/nextdotjs.svg", alt: "nextjs" },
    { src: "/icons/postgresql.svg", alt: "Postgresql" },
    { src: "/icons/react.svg", alt: "React" },
    { src: "/icons/redis.svg", alt: "Redis" },
    { src: "/icons/terraform.svg", alt: "Terraform" },
  ];
</script>

<div class="overflow-hidden relative w-full py-6">
  <div class="flex items-center will-change-transform animate-slide w-max">
    <!-- Duplicate the icon list to create seamless looping -->
    {#each [...icons, ...icons] as icon, i (icon.src + Math.random())}
      <img
        aria-hidden={i > icons.length - 1}
        src={asset(icon.src)}
        alt={icon.alt}
        class="h-12 w-12 mx-6 opacity-70 hover:opacity-100 transition-opacity hover:animate-wiggle"
      />
    {/each}
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


    .animate-slide {
        animation: slide 20s linear infinite;
    }

    .animate-slide:hover {
        animation-play-state: paused;
    }
</style>