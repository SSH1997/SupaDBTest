<script lang="ts">
    import { onMount } from "svelte";
    import { createClient } from "@supabase/supabase-js";
    import { SectionContent, type Day } from "@/utils/types";
    import { supabaseUrl, supabaseKey } from "@/utils/dbAuth";
    import Calendar from "../molecules/Calendar.svelte";

    export let currentSectionContent: SectionContent;

    const conn = createClient(supabaseUrl, supabaseKey);

    onMount(async() => {
        // TODO: DB 모듈로 분리하기
        const { data, error } = await conn
        .from("TESTDB")
        .select();
    });
</script>

<section class="section">
    {#if currentSectionContent == SectionContent.a}
        <Calendar />
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
</style>
