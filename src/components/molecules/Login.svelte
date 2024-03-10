<script lang="ts">
    import { onMount } from "svelte";
    import Button from "../atoms/Button.svelte";
    import { SectionContent } from "@/utils/types";

    export let setSectionContent: (sectionContent: SectionContent) => void;

    let totalPassCode: string;
    let totalPassCodeDigit: string;

    onMount(() => {
        initPassCode();
    });

    const initPassCode = () => {
        totalPassCode = "";
        totalPassCodeDigit = "______";
    }

    const insertPassCode = (passCode: string) => {
        totalPassCode += passCode;

        var splitedDigits = totalPassCodeDigit.split("");
        splitedDigits.unshift("*");
        splitedDigits.pop();
        totalPassCodeDigit = splitedDigits.join("");
    }

    const submitPassCode = () => {
        if (totalPassCode == "▲▲▲▲▲▲") {
            setSectionContent(SectionContent.Calendar);
        } else {
            alert("비밀번호가 틀렸습니다!");
            initPassCode();
        }
    }
</script>

<div>
    <div>
        {totalPassCodeDigit}
    </div>

    <div>
        <Button buttonText="▲" onClick={() => insertPassCode("▲")}></Button>
    </div>
    <div style="display: flex;">
        <Button buttonText="◀︎" onClick={() => insertPassCode("◀︎")}></Button>
        <Button buttonText="▼" onClick={() => insertPassCode("▼")}></Button>
        <Button buttonText="▶︎" onClick={() => insertPassCode("▶︎")}></Button>
    </div>
    <Button buttonText="Submit" onClick={submitPassCode}></Button>
</div>

<style>
</style>
