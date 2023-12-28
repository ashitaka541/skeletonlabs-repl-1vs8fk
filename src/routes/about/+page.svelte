<script>
    import ClickableHeader from './ClickableHeader.svelte';
    import TypewriterEffect from './TypewriterEffect.svelte';

    let activeSection = null;
    let activatedSections = new Set();

    const sections = {
        
    'Our Mission': {
            fullText: 'To revolutionize ending homelessness with trauma-informed, evidence-based, client-directed services. Leveraging AI, data analysis, and SCRUM lean project management, we aim for continuously improving solutions that empower a transition from homelessness to stability and fulfillment.',
            summary: 'To revolutionize the approach to end homelessness.'
        },
        'Our Values': {
            fullText: 'Founded on empathy, evidence, and empowerment, our organization prioritizes a trauma-informed approach and evidence-based solutions. We empower clients through collaborative SMART goal setting for specific, measurable, and achievable outcomes. Our inclusive, low-barrier approach ensures wide-reaching service accessibility. We emphasize community collaboration and agile responsiveness, constantly adapting to evolving needs, driving progress toward a future where homelessness is a solvable challenge.',
            summary: 'Empathy, Evidence, and Empowerment at our core.'
        },
        'Our Vision': {
            fullText: 'Envisioning a world where homelessness is a solvable challenge, we aim to create a compassionate, efficient, and data-driven ecosystem. Our vision focuses on providing individuals with the tools, skills, and resources needed to rebuild their lives with dignity and purpose.',
            summary: 'A world where homelessness is solvable.'
        },
        'Our Programs': {
            fullText: 'Our suite of programs empowers individuals through Core Curriculum Development in job, social, technical, and life skills, delivered via a flexible hybrid model for accessibility. Our Resource Connection Hub, Digital Access Center, and Health and Hygiene Facilities offer essential support, while partnerships enhance personal care services. We integrate AI and Data Analysis for service refinement and employ SCRUM Lean Project Management for efficiency. Continuous Feedback and Improvement, coupled with Community Engagement and Empowerment, form our holistic approach for long-term stability and independence.',
            summary: 'Comprehensive programs for empowerment and independence.'
        }
    
    };

    function showSection(section) {
        if (activeSection !== section) {
            activatedSections.add(section);
        }
        activeSection = section;
    }

    function displayText(section) {
    if (activeSection === section) {
        return sections[section].fullText; // Full text for the active section
    } else if (activatedSections.has(section)) {
        return sections[section].summary; // Summary for activated sections
    }
    return ''; // Nothing for non-activated sections
}
</script>

<div class="container h-full mx-auto flex justify-center items-center">
    <div class="space-y-10 text-center flex flex-col items-center">
        {#each Object.keys(sections) as section}
            <div class="section">
                <ClickableHeader 
                    title={section} 
                    on:click={() => showSection(section)} 
                    active={activeSection === section} />
                <TypewriterEffect text={displayText(section)} speed={2} />
            </div>
        {/each}
    </div>
</div>

<style>
    .container {
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .section {
        text-align: center;
    }
</style>
