<script>
    import { createEventDispatcher } from 'svelte';

    export let title = '';
    export let active = false;
    const dispatch = createEventDispatcher();

    function handleClick() {
        dispatch('click');
    }
</script>

{#if active}
    <h2 tabindex="0" on:click={handleClick} class="clickable-title h2 font-bold">
        {title}
    </h2>
{:else}
    <h3 tabindex="0" on:click={handleClick} class="clickable-title h3">
        {title}
    </h3>
{/if}
