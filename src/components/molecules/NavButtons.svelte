<script lang="ts">
    import Button from "@/components/atoms/Button.svelte";
    import { SectionContent } from "@/utils/types";

    export let setSectionContent: (sectionContent: SectionContent) => void;

    const sectionContentList =
        Object.values(SectionContent)
        .filter(it => typeof it === "string") as SectionContent[];
</script>

<div class="nav_buttons_outer_div">
    {#each sectionContentList as sectionContent}
        <div class="nav_buttons_inner_div">
            <Button buttonText={sectionContent.toString()} onClick={() => setSectionContent(sectionContent)} />
        </div>
    {/each}
</div>

<style>
    .nav_buttons_outer_div {
        width: 100%;

        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .nav_buttons_inner_div {
        width: 20%;

        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>
