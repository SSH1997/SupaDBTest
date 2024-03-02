<script lang="ts">
    import MenuButton from "@/components/molecules/HeaderMenuButton.svelte";

    export let toggleNav: () => void;
</script>

<header class="header">
    <p>👾 Digivice 👾</p>
    <MenuButton {toggleNav} />
</header>

<style>
    .header {
        position: fixed;
        top: 0;

        width: 100vw;
        height: 6vh;
        
        background-color: color(srgb 0.3482 0.4661 0.3776);

        z-index: 1;

        display: flex;
        align-items: center;
        justify-content: space-between;

        padding: 1vh;
        box-sizing: border-box;

        font-size: 4vh;
    }
</style>
