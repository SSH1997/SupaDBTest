<script lang="ts">
    import { onMount } from "svelte";
    import { type Day } from "@/utils/types";
    import Button from "../atoms/Button.svelte";

    let currentYear: number;
    let currentMonth: number;
    let days: Day[];

    onMount(() => {
        const date = new Date();
        InitDays(date.getFullYear(), date.getMonth() + 1);
    })

    const InitDays = (year: number, month: number) => {
        days = [
            {day: 1, content: ["a", "b", "c"]},
            {day: 2, content: ["d", "e", "f"]}
        ];

        AddDays(year, month);
    }

    const AddDays = (year: number, month: number) => {
        const date = new Date(year, month - 1, 1);
        var day = date.getDay();
        var contentLength = days.length;
        for (let index = 0; index < day - 1; index++) {
            days.unshift({ day: 0, content: [] });
        }
        const length = days.length;
        for (let index = 0; index < 42 - length; index++) {
            var z = new Date(year, month - 1, contentLength + index + 1);
            if (z.getMonth() + 1 == month) {
                days.push({ day: contentLength + index + 1, content:[] });
            }
        }

        currentYear = year;
        currentMonth = month;
    }

    const changeMonth = (direction: number) => {
        currentMonth += direction;

        if (currentMonth % 13 == 0) {
            currentYear += direction;
            currentMonth = (13 + direction) % 13;
        }
        
        InitDays(currentYear, currentMonth);
    }
</script>

<div>
    <div class="monthPicker">
        <div class="changeMonthButton">
            <Button buttonText="◀︎" onClick={() => {changeMonth(-1)}}/>
        </div>
        <div class="currentMonth">
            {currentYear}년 {currentMonth}월
        </div>
        <div class="changeMonthButton">
            <Button buttonText="▶︎" onClick={() => {changeMonth(1)}}/>
        </div>
    </div>
    <div class="dayIndicator">
        <div class="dayHeader">월</div>
        <div class="dayHeader">화</div>
        <div class="dayHeader">수</div>
        <div class="dayHeader">목</div>
        <div class="dayHeader">금</div>
        <div class="dayHeader">토</div>
        <div class="dayHeader">일</div>
    </div>
    <div class="days">
        {#if days != null}
            {#each days as day}
                <div class="day">
                    <div class="dayHeader">
                        {#if day.day != 0}
                            {day.day}
                        {/if}
                    </div>
                    <div class="dayContent">
                        {#each day.content as content}
                            <p>- {content}</p>
                        {/each}
                    </div>
                </div>
            {/each}
        {/if}
    </div>
</div>

<style>
    .monthPicker {
        height: 5vh;
        background-color: brown;
        display: flex;
        justify-content: space-evenly;
    }

    .changeMonthButton {
        width: 10vw;
        padding: 0;
        margin: 0;
        height: 5vh;
        display: flex;
    }

    .currentMonth {
        font-size: 4vh;
        line-height: 1.5;
    }

    .dayIndicator {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    }

    .days {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    }

    .day {
        height: 10vh;
        background-color: aqua;
    }

    .dayHeader {
        height: 2vh;
        background-color: violet;
        border: 1px solid black;
        font-size: 2vh;
    }

    .dayContent {
        height: 8vh;
        border: 1px solid black;
    }

    .dayContent p {
        font-size: 2vh;
        margin: 0;
    }
</style>
