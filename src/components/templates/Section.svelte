<script lang="ts">
    import { onMount } from "svelte";
    import { createClient } from "@supabase/supabase-js";
    import { SectionContent, type Day } from "@/utils/types";
    import { supabaseUrl, supabaseKey } from "@/utils/dbAuth";

    import Login from "../molecules/Login.svelte";
    import Calendar from "../molecules/Calendar.svelte";

    export let currentSectionContent: SectionContent;
    export let setSectionContent: (sectionContent: SectionContent) => void;

    // const conn = createClient(supabaseUrl, supabaseKey);

    onMount(async() => {
        // TODO: DB 모듈로 분리하기
        // const { data, error } = await conn
        // .from("TESTDB")
        // .select();
    });
</script>

<section class="section">
    {#if currentSectionContent == SectionContent.Login}
        <Login {setSectionContent} />
    {/if}
    {#if currentSectionContent == SectionContent.Calendar}
        <Calendar />
    {/if}
</section>

<style>
    section {
        position: absolute;
        top: 0;

        width: 100vw;

        background-color: white;
        
        z-index: 0;
        
        padding: 6vh 1vh 1vh 1vh;
        box-sizing: border-box;
    }
</style>
