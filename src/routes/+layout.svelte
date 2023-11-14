<script lang=ts>
    import LogoLinkedin from 'carbon-icons-svelte/lib/LogoLinkedin.svelte';
    import LogoGithub from "carbon-icons-svelte/lib/LogoGithub.svelte";
    import LogoInstagram from "carbon-icons-svelte/lib/LogoInstagram.svelte";
    import '../global.css';
    import { fly, fade } from 'svelte/transition';
    import { onMount } from 'svelte';
    import { page } from '$app/stores';

    $: route = $page.url.pathname.split('/').pop();

      let visible = false;
      onMount(() => {
        visible = true;
      })
</script>

<svelte:head>
    <title>Colin B</title>
    <meta property='og:title' content='Colin B' />
    <meta property='og:image' content='https://www.colinedwin.com/facebookShare.webp' />
    <meta property='og:image:alt' content='Text reading howdy' />
    <meta property='og:description' content="Colin's Portfolio" />
    <meta property='og:type' content='website' />
    <meta property='og:url' content="https://colinedwin.com" />

</svelte:head>
<div class=page>
    {#if visible}
    <nav in:fly={{duration: 500, y: -100}}>
        <a href='/' class={!route ? 'current' : ''}>ABOUT</a>
        <a href='/portfolio' class={route === 'portfolio' ? 'current' : ''}>PORTFOLIO</a>
        <a href='/resume' class={route === 'resume' ? 'current' : ''}>RESUME</a>
    </nav>
    <main >
        <slot />
    </main>
    {/if}
    {#if visible}
    <footer in:fade={{duration: 1000}}>
        <a href='https://github.com/soundproofboot' target=_blank><LogoGithub size={32}/></a>
        <a href='https://www.linkedin.com/in/colin-bares-3296b6224/' target=_blank><LogoLinkedin size={32}/></a>
        <a href='https://www.instagram.com/colinedwinbares/' target=_blank><LogoInstagram size={32}/></a>
    </footer>
    {/if}
</div>

<style>
    .page {
        display: flex;
        flex-direction: column;
        min-height: 100dvh;
    }
    nav, footer {
        display: flex;
        width: 100%;
        background-color: rgba(0,0,0,.6);
        height: 5vh;
        align-items: center;
    }

    nav {
        justify-content: space-evenly;
        top: 0;
        z-index: 1;
        position: sticky;
        padding: .5em 0;
    }

    nav a {
        color: #ccc;
        font-size: 1.5em;
    }

    .current {
        font-weight: bold;
        color: #fff;
        text-shadow: 2px 2px 2px gray;
        transform: scale(1.2);
        transition: .25s;
    }

    footer {
        justify-content: center;
        position: sticky;
        bottom: 0;
        padding: .5em 0;
    }


    a {
        text-decoration: none;
    }
    footer a {
        margin: 0 1em;
        color: green;
        display: grid;
        place-content: center;
        opacity: .5;
        transition: .5s;
    }

    footer a:hover {
        opacity: 1;
    }


    :global(footer a svg) {
        fill: white;
    }
    main {
        flex: 1;
        display: grid;
        place-content: center;
    }
</style>