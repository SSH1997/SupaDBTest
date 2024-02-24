<script lang="ts">
    import { afterUpdate } from "svelte";
    import { createClient } from "@supabase/supabase-js";
    import { SectionContent, type Day } from "@/utils/types";
    import { supabaseUrl, supabaseKey } from "@/utils/dbAuth";

    export let currentSectionContent: SectionContent;

    const conn = createClient(supabaseUrl, supabaseKey);

    let days: Day[];

    afterUpdate(async () => {
        const { data, error } = await conn
        .from("TESTDB")
        .select();

        days = [
            {content: ["a", "b", "c"]},
            {content: ["d", "e", "f"]},
            {content: ["g", "h", "i"]},
        ];

        AddDays();
    });

    const AddDays = () => {
        const length = days.length;

        for (let index = 0; index < 35 - length; index++) {
            days.push({ content:[] });
        }
    }
</script>

<section class="section">
    <!-- 추후에 molecules 로 빼야함-->
    {#if currentSectionContent == SectionContent.a}
        <div class="days">
        {#each days as day}
            <div class="day">
                {#each day.content as content}
                    <p>{content}</p>
                {/each}
            </div>
        {/each}
        </div>
    {/if}
</section>

<style>
    section {
        position: absolute;
        top: 0;

        height: 100vh;
        width: 100vw;

        background-color: green;
        
        z-index: 0;
        
        padding: 6vh 1vh 1vh 1vh;
        box-sizing: border-box;
    }

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
