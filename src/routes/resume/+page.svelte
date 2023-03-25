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
    <h1>Skills</h1>
<ul>
    <li>Recent experience on large projects built with 
        <ul>
            <li><strong>SvelteKit</strong> & <strong>MongoDB</strong> w/ <strong>TypeScript</strong></li>
            <li><strong>Next.js</strong> & <strong>SQLite</strong> w/ <strong>TypeScript</strong></li>
            <li><strong>React</strong> w/ <strong>Supabase</strong> & <strong>Material UI</strong> w/ <strong>TypeScript</strong></li>
        </ul>
    <li>Well versed in the usual suspects - </li>
    <ul>
        <li>
            <strong>HTML5</strong>
        </li>
        <li>
            <strong>CSS3</strong>
        </li>
        <li>
            <strong>JavaScript ES6</strong>
        </li>
        <li>Version control w/ <strong>GitHub</strong> & <strong>Bitbucket</strong></li>
        <li>Agile development w/ <strong>Jira</strong> & <strong>Asana</strong></li>
    </ul>
    <li>RESTful APIs with <strong>Express.js</strong></li>
    <li>Cloud - some experience with 
        <ul>
            <li><strong>AWS</strong></li>
            <li><strong>Vercel</strong></li>
            <li><strong>Google Cloud Platform</strong></li>
            <li><strong>Heroku</strong></li>
        </ul>
</ul>
<p style='text-align: center;'>You can find my full resume <a href='https://drive.google.com/file/d/1fmxthz63-iYAEdHYjbZmhPN5WnRJbEE6/view?usp=sharing' target=_blank>here</a></p>
</section>
{/if}
<style>
    section {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
    }
    h1 {
        text-align: center;
        margin-bottom: 0;
    }

    ul  {
        list-style-type: none;
        margin: 1em 0;
        padding-inline-start: 1em;
    }
    li {
        /* margin: .5em 0; */
    }
</style>