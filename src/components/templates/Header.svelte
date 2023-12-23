<script lang="ts">
    import MenuButton from "@/components/molecules/HeaderMenuButton.svelte";

</script>

<header class="header">
    <p>Header</p>
    <MenuButton />
</header>

<style>
    .header {
        position: fixed;
        top: 0;

        width: 100vw;
        height: 6vh;
        
        background-color: gray;

        z-index: 1;

        display: flex;
        align-items: center;
        justify-content: space-between;

        padding: 1vh;
        box-sizing: border-box;
    }
</style>
