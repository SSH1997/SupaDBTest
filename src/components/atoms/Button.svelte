<script lang="ts">
    export let buttonText: string = "";
    export let imgSrc: string = "";
    export let onClick: (e: MouseEvent) => void;
</script>

<button on:click={onClick} class="atom_button">
    <img src="{imgSrc}" alt="{buttonText}">
    {buttonText}
</button>

<style>
    .atom_button {
        width: 100%;
        height: 100%;
    }
</style>
