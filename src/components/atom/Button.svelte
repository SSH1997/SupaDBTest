<script lang="ts">
    export let buttonText: string;
    export let onClick: (e: MouseEvent) => void;
    
    let buttonRef:HTMLButtonElement;
</script>

<button bind:this={buttonRef} on:click={onClick}>{buttonText}</button>

<style>
</style>
