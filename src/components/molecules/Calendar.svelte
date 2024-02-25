<script lang="ts">
    import { onMount } from "svelte";
    import { type Day } from "@/utils/types";

    let days: Day[];

    onMount(() => {
        days = [
            {content: ["a", "b", "c"]},
            {content: ["d", "e", "f"]},
            {content: ["g", "h", "i"]},
        ];

        AddDays();
    })

    const AddDays = () => {
        const length = days.length;

        for (let index = 0; index < 35 - length; index++) {
            days.push({ content:[] });
        }
    }
</script>

<div class="days">
    {#if days != null}
        {#each days as day}
        <div class="day">
            {#each day.content as content}
                <p>{content}</p>
            {/each}
        </div>
        {/each}
    {/if}
</div>

<style>
    .days {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    }

    .day {
        width: 50px;
        height: 50px;
        background-color: aqua;
        margin: 10px;
    }
</style>
