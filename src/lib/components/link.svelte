<script lang="ts">
    interface LinkProps {
        href: string;
        text: string;
    }

    let { href, text }: LinkProps = $props();
</script>

<a rel="noopener noreferrer" class="underline underline-offset-4 hover:underline-offset-6 transition-[text-underline-offset] duration-300" {href} target="_blank">{text}</a>

