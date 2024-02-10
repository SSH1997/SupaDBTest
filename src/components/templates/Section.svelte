<script lang="ts">
    import { afterUpdate } from "svelte";
    import { createClient } from "@supabase/supabase-js";
    import type { SectionContent } from "@/utils/types";
    import { supabaseUrl, supabaseKey } from "@/utils/dbAuth";

    export let currentSectionContent: SectionContent;

    const conn = createClient(supabaseUrl, supabaseKey);
    
    afterUpdate(async () => {
        const { data, error } = await conn
        .from("TESTDB")
        .select();

        if (error) throw error;
        console.log(data);
    });
</script>

<section class="section">
    <p>{currentSectionContent == null ? "" : currentSectionContent}</p>
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
