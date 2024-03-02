<script lang="ts">
    import NavButtons from "@/components/molecules/NavButtons.svelte";
    import type { SectionContent } from "@/utils/types";

    export let setSectionContent: (sectionContent: SectionContent) => void;
</script>

<nav class="nav">
    <NavButtons {setSectionContent} />
</nav>

<style>
    .nav {
        position: absolute;
        top: 6vh;

        height: 6vh;
        width: 100vw;

        background-color: cadetblue;

        z-index: 1;
    }
</style>
