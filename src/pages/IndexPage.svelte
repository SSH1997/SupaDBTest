<script lang="ts">
    import Footer from "@/components/templates/Footer.svelte";
    import Header from "@/components/templates/Header.svelte";
    import Nav from "@/components/templates/Nav.svelte";
    import Section from "@/components/templates/Section.svelte";

    let isNavVisible: boolean = false;

    const toggleNav = () => {
        isNavVisible = !isNavVisible;
    };

</script>

<div>
    <Header {toggleNav} />
    {#if isNavVisible}
        <Nav />
    {/if}
    <Section />
    <Footer />
</div>
