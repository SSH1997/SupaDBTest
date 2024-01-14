<script lang="ts">
    import Button from "@/components/atoms/Button.svelte";

    export let toggleNav: () => void;
</script>

<div class="header_menu">
    <Button onClick={toggleNav} imgSrc="https://ssh1997.github.io/SupaDBTest/assets/headerMenuButton.png"/>
</div>

<style>
    .header_menu {
        width: 4vh;
        height: 4vh;
    }
</style>
