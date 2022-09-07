<script>
    import { fly, scale, fade } from 'svelte/transition';
    import { quadOut } from 'svelte/easing';

    export let open = false;

    let links = [
        {
            title: "Home",
            link: "/Home",
        },
        {
            title: "Über uns",
            link: "/About",
        },
        {
            title: "Abi Aktion",
            link: "/Aktion",
        },
        {
            title: "Termine",
            link: "/Termine",
        }
    ]
</script>

{#if open}
    <div class="w-full h-full bg-slate-700 relativ -mt-10">
        {#each links as link, i}
            <p transition:fly={{ y: -15, delay: 50 * i }}>
                <a on:click="{() => open = !open}" href="{link.link}">{link.title}</a>
            </p>
        {/each}
    </div>

    <hr class="bg-slate-900" transition:scale={{ duration: 750, easing: quadOut, opacity: 1 }} />
{/if}

<style>
    :global(html) {
        background: #1d1d2f;
    }
    div {
        text-align: center;
        font-size: 1.5em;
        letter-spacing: 0.15em;
        padding: 2%;
        padding-top: 0;
        color: #eef;
    }
    p {
        cursor: pointer;
        width: max-content;
        margin: 1rem auto;
    }
    p:hover {
        text-decoration: underline;
    }

    hr {
        border: 0; 
        --tw-bg-opacity: 1;
        border-top: 1px solid rgb(15 23 42 / var(--tw-bg-opacity));
    }
</style>