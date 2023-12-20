<script lang="ts">
    let buttonRef:HTMLButtonElement;

    const onButtonClick = () => {
        alert("Hello! World!");
    }
</script>

<button bind:this={buttonRef} on:click={onButtonClick}>Button</button>

<style>

</style>