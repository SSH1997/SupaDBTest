<script lang="ts">
    import Button from "@/components/atoms/Button.svelte";
    import { SectionContent } from "@/utils/types";

    export let setSectionContent: (sectionContent: SectionContent) => void;
</script>

<div class="nav_buttons_outer_div">
    <div class="nav_buttons_inner_div">
        <Button buttonText={SectionContent[SectionContent.a]} onClick={() => setSectionContent(SectionContent.a)} />
        <Button buttonText={SectionContent[SectionContent.b]} onClick={() => setSectionContent(SectionContent.b)} />
        <Button buttonText={SectionContent[SectionContent.c]} onClick={() => setSectionContent(SectionContent.c)} />
    </div>
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
