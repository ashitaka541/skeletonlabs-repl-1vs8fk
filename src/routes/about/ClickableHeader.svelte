<script>
    import { createEventDispatcher } from 'svelte';

    export let title = '';
    export let active = false;
    const dispatch = createEventDispatcher();

    function handleClick() {
        dispatch('click');
    }
</script>

<div class="header-container">
    {#if active}
        <h2 tabindex="0" on:click={handleClick} class="clickable-title h2 font-bold">
            {title}
        </h2>
    {:else}
        <h3 tabindex="0" on:click={handleClick} class="clickable-title h3">
            {title}
        </h3>
    {/if}
</div>

<style>
    .header-container {
        text-align: center;
    }

    .clickable-title {
        margin: 0;
        padding: 1em;
        line-height: 1.2; /* Adjust as needed */
    }

    .h2, .h3 {
        /* If needed, add specific styles for h2 and h3 */
    }
</style>