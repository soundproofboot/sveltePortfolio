<script lang=ts>
    import { onMount } from 'svelte';
    import { fade } from 'svelte/transition';
    let index = 0;

    let projects = [
        {
            src: '/greenNeighbor.png',
            title: 'Green Neighbor Challenge',
            tech: 'Next.js/SQLite && SvelteKit/MongoDB',
            live: 'https://www.greenneighborchallenge.org/',
            repo: '',
            text: 'Maintained and expanded Next.js app with SQLite backend. Currently rebuilding in SvelteKit with MongoDB. Volunteer since 5/22, contract since 10/22.'
        },
        {
            src: '/conwaysGameOfLife.png',
            title: `Conway's Game of Life`,
            tech: 'SvelteKit && TypeScript',
            live: 'https://conways-game-of-life-seven.vercel.app/',
            repo: 'https://github.com/soundproofboot/conwaysGameOfLife',
            text: 'Browser based implementation of Conway\'s Game of Life built with SvelteKit and TypeScript'
        },
        {
            src: '/park.png',
            title: 'National Park Spotter',
            tech: 'React, MongoDB, GraphQL',
            live: 'https://pacific-brushlands-65513.herokuapp.com/',
            repo: 'https://github.com/SepidehAyani/national-parks-spotter',
            text: "Interactive U.S. Map showing all National Parks and details about them. User's can register, leave comments, and save a list of parks for future visits"
        },
        {
            src: '/pixelArt.png',
            title: 'Pixel Art',
            tech: 'Svelte',
            live: 'https://pixel-art-sage.vercel.app/',
            repo: 'https://github.com/soundproofboot/pixelArt',
            text: 'Simple pixel art creator using native color input and touch events for mobile compatability'
        },
        {
            src: 'fav-mates.png',
            title: 'Fav Mates',
            tech: 'Express, MySQL, Handlebars',
            live: 'https://lit-mountain-78827.herokuapp.com/',
            repo: 'https://github.com/Nate-Huerd/Fav-Mates',
            text: "Food delivery app allowing user's to place orders from mock restaurants."
        },
        {
            src: 'popcorn.png',
            title: 'Popcorn!',
            tech: 'fetchAPI, Bulma',
            live: 'https://crosenfrisk.github.io/Popcorn/',
            repo: 'https://github.com/crosenfrisk/Popcorn',
            text: "Popcorn! is a mobile-friendly application that helps users connect with new content based on personalized keyword searches, genres selected, and trending shows / movies according to two open source APIs: Online Movie Database and The Movie DB."
        }
    ]

    let visible = false;

    onMount(() => {
        visible = true;
    })
</script>
{#if visible}
<section in:fade={{duration: 500}}>
<button on:click={() => {
    if (index > 0) {
        index -= 1
    } else index = projects.length -1;
}}><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--! Font Awesome Pro 6.3.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. --><path d="M9.4 233.4c-12.5 12.5-12.5 32.8 0 45.3l160 160c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L109.2 288 416 288c17.7 0 32-14.3 32-32s-14.3-32-32-32l-306.7 0L214.6 118.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0l-160 160z"/></svg></button>
{#each projects as project, i}
    {#if index === i}
    {@const {src, title, tech, live, repo, text} = project}
    <div class=project
     >
        <a href={live} target=_blank class=imgContainer>
            <img {src} alt='screenshot of website on mobile device'>
        </a >
        <div in:fade={{duration: 50}} class=projectText>
            <h2 class=titleLine>{title}</h2>
            <p class=techLine>{tech}</p>
            <div class=linkLine>
                <a href={live} target=_blank>LIVE</a>
                {#if repo}
                <a href={repo} target=_blank>REPO</a>
                {/if}
            </div>
            <p class=text>{text}</p>
        </div>
    </div>
    {/if}
{/each}
<button on:click={() => {
    if (index < projects.length -1) {
        index += 1;
    } else {
        index = 0
    }
}}>
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><!--! Font Awesome Pro 6.3.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. --><path d="M438.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-160-160c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3L338.8 224 32 224c-17.7 0-32 14.3-32 32s14.3 32 32 32l306.7 0L233.4 393.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0l160-160z"/></svg>
</button>
</section>
{/if}

<style>
    section {
        display: flex;
        justify-content: space-between;
        height: 80vh;
    }

    .project {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 80vw;
    }

    .imgContainer {
        width: 50%;
        display: flex;
        justify-content: center;
    }

    .project img {
        border-radius: 1em;
        border: 1px solid #000;
        outline: 3px solid #ececec;
        width: 80%;
        filter: brightness(.95);
        transform: scale(.98);
        transition: .5s;
    }

    .project img:hover {
        filter: brightness(1.05);
        transform: scale(1);
        cursor: pointer;
    }

    .projectText {
        width: 100%;
    }

    .titleLine {
        text-align: center;
        margin-bottom: 0;
    }

    .techLine {
        text-align: center;
        margin-top: 0;
    }

    .linkLine {
        text-align: center;
        display: flex;
        justify-content: space-evenly;
        flex-wrap: wrap;
    }

    .linkLine a {
        background-color: gray;
        padding: .5em;
        border-radius: 5px;
        text-decoration: none;
        text-shadow: 0px 0px 5px black;
        outline: 2px solid white;
        color: white;
    }

    .text {
    }
    button {
        all: unset;
        width: 30px;
        opacity: .5;
        transition: .5s;
    }

    button:hover {
        cursor: pointer;
        opacity: 1;
    }

    svg {
        fill: white;
    }

    @media screen and (min-width: 768px) {

        .project {
            flex-direction: row;
            width: 90vw;
            align-items: normal;
        }

        .project img {
            height: 100%;
            width: auto;
        }

        .projectText {
            margin: 2em;
            width: 50%;
        }

        .linkLine {
            margin: 2em 0;
        }

        .text {
            margin: 3em 3em 0 3em;
        }
    }
</style>