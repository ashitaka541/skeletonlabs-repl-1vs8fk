<script>
    import { writable } from 'svelte/store';

    export let fullText;
    export let summary;
    export let speed = 1;
    export let reverse = false;

    const text = writable('');
    let isComplete = false;

    function typewriter(node, { speed, reverse }) {
        const targetText = reverse ? summary : fullText;
        const duration = targetText.length * (100 / speed);
        text.set('');

        return {
            duration,
            tick: (t) => {
                const i = Math.trunc(targetText.length * t);
                text.set(targetText.slice(0, i));
                if (i === targetText.length) {
                    isComplete = true;
                }
            },
            css: (t) => `opacity: ${t}`
        };
    }

    // No additional reactive statement is needed
</script>

<p transition:typewriter={{ speed, reverse }}>
    {$text}
</p>