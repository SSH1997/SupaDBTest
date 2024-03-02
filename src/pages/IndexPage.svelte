<script lang="ts">
    import Footer from "@/components/templates/Footer.svelte";
    import Header from "@/components/templates/Header.svelte";
    import Nav from "@/components/templates/Nav.svelte";
    import Section from "@/components/templates/Section.svelte";
    import { SectionContent } from "@/utils/types";

    let isNavVisible: boolean = false;
    let currentSectionContent: SectionContent = SectionContent.Calendar;

    const toggleNav = () => {
        isNavVisible = !isNavVisible;
    };

    const setSectionContent = (sectionContent: SectionContent) => {
        currentSectionContent = sectionContent;
        isNavVisible = false;
    }

</script>

<div>
    <Header {toggleNav} />
    {#if isNavVisible}
        <Nav {setSectionContent} />
    {/if}
    <Section {currentSectionContent} />
    <Footer />
</div>
