<script>
    import ProjectCard from "./projectCard.svelte";
    import Modal from "./modal.svelte";
    import { fade } from "svelte/transition";
    import GoInbox from 'svelte-icons/go/GoInbox.svelte';
    import DiGithubBadge from 'svelte-icons/di/DiGithubBadge.svelte';

    let props = $props();

    let showModal = $state(false);

    import "../../app.css";

    //TODO -> IMPLEMENT PROJECT FILTER/SEARCH

</script>

<main>
    {#if props.jobs }
        <ul class="navContainer">
            <li>
                <a href="https://binaryconfidence.com">QA Lead @ Binary Confidence</a>
            </li>
        </ul>
    {:else if props.projects}
        <ul class="navContainer">
            <div transition:fade>
                <ProjectCard 
                    name="BottleBuddy" 
                    itemName="project"
                    projectType="mobile app" 
                    description="Wolt-like delivery&pickup app for plastic bottles"
                    checked="checked"
                    repo="https://github.com/Baarneeyy/BottleBuddy"
                    stack = 'react-expo-pocketbase'
                    descrip="Develop & Implement Order screen -&gt ver0.1.0 done"
                
                />
                <ProjectCard 
                    name="Maestro" 
                    itemName="project"
                    projectType="web-app"
                    description="Utility website '100 gadgets' style"
                    repo="https://github.com/Baarneeyy/maestro"
                    stack = 'svelte'
                    descrip="Create unit converter"
                />
            </div>
        </ul>
    {:else if props.socials}
        <div class="btnPair">
            <a class="btn btn-secondary mr-4" role="button" href="https://github.com/Baarneeyy">
                <DiGithubBadge/>
            </a>
            <button class="btn" disabled="disabled">github: u/Baarneey</button>
        </div>
        <div class="btnPair">
            <button class="btn btn-secondary mr-4" onclick={() => (showModal = true)}>
                <GoInbox/>
            </button>
            <button class="btn" disabled="disabled">mail: tomas@vsetecka.sk</button>
        </div>
        <Modal bind:showModal/>
    {/if}
</main>

<style>
    .btnPair {
        display: flex;
        flex-direction: row;
        padding: 6px;
    }
</style>