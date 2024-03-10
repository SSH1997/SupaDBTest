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
        totalPassCodeDigit = "_ _ _ _ _ _";
    }

    const insertPassCode = (passCode: string) => {
        totalPassCode += passCode;

        var splitedDigits = totalPassCodeDigit.split(" ");
        splitedDigits.unshift("*");
        splitedDigits.pop();

        if (splitedDigits.every(it => it == "*")) {
            submitPassCode();
        }
        else {
            totalPassCodeDigit = splitedDigits.join(" ");
        }
    }

    const submitPassCode = () => {
        if (totalPassCode == "AABCCD" || totalPassCode == "BCDABC") {
            var date = new Date();
            var hour = date.getHours();
            var storedPassCode = localStorage.getItem("DigivicePassedHour");

            if (storedPassCode == null || Number.parseInt(storedPassCode) != hour) {
                localStorage.setItem("DigivicePassedHour", hour.toString());   
            }

            setSectionContent(SectionContent.Calendar);
        } else {
            alert("비밀번호가 틀렸습니다!");
            initPassCode();
        }
    }
</script>

<div>
    <img class="digivice_background" src="https://ssh1997.github.io/SupaDBTest/Digivice.webp" alt="" />

    <div class="passcode_zone">
        <div class="left_passcode_div">
            <Button buttonText="" onClick={() => insertPassCode("A")}></Button>
            <Button buttonText="" onClick={() => insertPassCode("B")}></Button>
        </div>
        <div class="middle_passcode_div">
            <div class="passcode_digit_background" />
            <div class="passcode_digit">
                {totalPassCodeDigit}
            </div>
        </div>
        <div class="right_passcode_div">
            <Button buttonText="" onClick={() => insertPassCode("C")}></Button>
            <Button buttonText="" onClick={() => insertPassCode("D")}></Button>
        </div>
    </div>
</div>

<style>
    .digivice_background {
        position: absolute;
        width: 100vw;
        top: 22vh;
    }

    .passcode_zone {
        position: absolute;
        top: calc(22vh + 8vw);
        
        width: 100vw;
        height: 59vw;

        display: flex;
    }

    .left_passcode_div {
        display: flex;
        flex-direction: column;

        width: 30%;
    }

    .middle_passcode_div {
        width: 40%;
        height: 100%;
    }

    .passcode_digit_background {
        position: absolute;
        top: 45%;
        left: 35%;
        width: 30vw;
        height: 30vw;

        border-radius: 10%;

        background-color: rgb(97, 104, 88);
    }

    .passcode_digit {
        position: absolute;
        top: 65%;
        left: 37%;
        font-size: 6vw;
    }

    .right_passcode_div {
        display: flex;
        flex-direction: column;

        width: 30%;
        height: 59%;
        padding-top: 24%;
    }
</style>
