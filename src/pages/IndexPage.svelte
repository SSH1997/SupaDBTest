<script lang="ts">
    import Footer from "@/components/templates/Footer.svelte";
    import Header from "@/components/templates/Header.svelte";
    import Nav from "@/components/templates/Nav.svelte";
    import Section from "@/components/templates/Section.svelte";
    import { SectionContent } from "@/utils/types";
    import { onMount } from "svelte";

    let isNavVisible: boolean = false;
    let currentSectionContent: SectionContent = SectionContent.Login;

    onMount(() => {
        var date = new Date();
        var hour = date.getHours();
        var passedHour = localStorage.getItem("DigivicePassedHour");
        
        if (passedHour != null && Number.parseInt(passedHour) == hour) {
            currentSectionContent = SectionContent.Calendar;
        }
    });

    const toggleNav = () => {
        isNavVisible = !isNavVisible;
    };

    const setSectionContent = (sectionContent: SectionContent) => {
        currentSectionContent = sectionContent;
        isNavVisible = false;
    }

</script>

<div>
    {#if currentSectionContent != SectionContent.Login}
        <Header {toggleNav} />
        <meta name="theme-color" content="color(srgb 0.3482 0.4661 0.3776)">

        {#if isNavVisible}
            <Nav {setSectionContent} />
        {/if}

        <Footer />
    {/if}

    <Section {currentSectionContent} {setSectionContent} />
</div>

<style>
    * {
        touch-action: manipulation;
    }
</style>