<script>
    export let text;
    export let speed = 1;

    // Typewriter effect function
    function typewriter(node, { speed }) {
        const duration = text.length * (100 / speed);

        return {
            duration,
            tick: (t) => {
                const i = Math.trunc(text.length * t);
                node.textContent = text.slice(0, i);
            }
        };
    }
</script>

<div class="text-container">
    <p transition:typewriter={{ speed }}>
        {text}
    </p>
</div>

<style>
    .text-container {
        width: 100%; /* Adjust as needed */
        text-align: center;
    }
</style>
