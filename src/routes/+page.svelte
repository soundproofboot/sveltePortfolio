<script lang=ts>
    import { onMount } from "svelte";
    import { fade } from 'svelte/transition';


    let visible = false;

    onMount(() => {
        visible = true;
    })
</script>

{#if visible}
<section in:fade={{duration: 500}}>
    <figure>
        <img src='./self.jpg' alt='A smiling man holding a corn dog'/>   
        <figcaption>Colin posing with a delicious corn dog</figcaption>
    </figure>
    <article>
        <h2>Dear interested party,</h2>
        <p>I'm a full stack developer based in Minneapolis, MN. My past experience in both physical inventory and music has prepared me to combine creativity with attention to detail. I'm most interested in exploring the places where the arts meet technology.</p>
        <p>Sincerely,</p>
        <strong>Colin Edwin Bares</strong>
    </article>
</section>
{/if}
<style>

    section {
        display: flex;
        /* align-items: center; */
        flex-direction: column;
    }

    figure {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    img {
        width: min(100%, 600px);
        border-radius: 5%;
        box-shadow: -1px 1px 5px rgba(128, 128, 128, 0.5), 1px -1px 5px rgba(255, 255, 255, 0.5);
    }

    figcaption {
        font-style: italic;
        margin-top: 1em;
    }

    article {
        /* display: grid;
        place-content: center; */
    }

    h2 {
        margin: 0 0 0 1em;
    }

    p, strong {
        margin: 1em 1em 0 1em;
    }

    strong {
        margin-top: 0;
    }
    @media screen and (min-width: 728px) {
        section {
            flex-direction: row;
        }

        figure {
            width: 50%;
        }

        article {
            padding: 0 3em;
            width: 50%;
            margin-top: 2em;
        }
    }
</style>