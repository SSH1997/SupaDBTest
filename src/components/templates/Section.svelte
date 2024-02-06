<script lang="ts">
  import type { SectionContent } from "@/utils/types";

    export let currentSectionContent: SectionContent;
</script>

<section class="section">
    <p>{currentSectionContent == null ? "" : currentSectionContent}</p>
</section>

<style>
    section {
        position: absolute;
        top: 0;

        height: 100vh;
        width: 100vw;

        background-color: green;
        
        z-index: 0;
        
        padding: 6vh 1vh 1vh 1vh;
        box-sizing: border-box;
    }
</style>
