<script lang="ts">
    import Button from "@/components/atoms/Button.svelte";
    import { SectionContent } from "@/utils/types";

    export let setSectionContent: (sectionContent: SectionContent) => void;
</script>

<div class="nav_buttons_outer_div">
    <div class="nav_buttons_inner_div">
        <Button buttonText={SectionContent[SectionContent.Calendar]} onClick={() => setSectionContent(SectionContent.Calendar)} />
    </div>
    <div class="nav_buttons_inner_div">
        <Button buttonText={SectionContent[SectionContent.Etc]} onClick={() => setSectionContent(SectionContent.Etc)} />
    </div>
</div>

<style>
    .nav_buttons_outer_div {
        width: 100%;

        display: flex;
        align-items: center;
    }

    .nav_buttons_inner_div {
        margin: 0.45vh 3vw;
        background-color: aliceblue;
        padding: 0.2vh 2vw;
        border-radius: 10px;
    }
</style>
