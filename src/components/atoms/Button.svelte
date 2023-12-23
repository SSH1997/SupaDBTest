<script lang="ts">
    export let buttonText: string = "";
    export let imgSrc: string = "";
    export let onClick: (e: MouseEvent) => void;
</script>

<button on:click={onClick} class="atom_button">
    <img class="atom_button_image" src="{imgSrc}" alt="{buttonText}">
    {buttonText}
</button>

<style>
    .atom_button {
        width: 100%;
        height: 100%;
        padding: 0;
        border: none;
    }

    .atom_button_image {
        width: 100%;
        height: 100%;
    }
</style>
