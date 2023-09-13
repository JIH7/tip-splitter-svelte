<script lang="ts">
    import ButtonPanel from "./ButtonPanel.svelte";
    import IconDollar from "../assets/icon-dollar.svg";
    import IconPerson from "../assets/icon-person.svg";

    import { onMount } from "svelte";
    
    const maxlength = 16;

    export let bill:number | null = null;
    export let tipPercent:number | null = null;
    export let people:number | null = null;
    export let calculate:Function;
    export let buttonPanelSelection:number | null = 0;

    const enforceMaxLength = ( e:Event , input:HTMLInputElement, length:number ) => {
        if (input.value.toString().length >= length) {
            e.preventDefault();
        }
    }

    onMount(() => {
        const inputs:NodeListOf<HTMLInputElement> = document.querySelectorAll("h2 > input[type=number]");
        const billInput:HTMLInputElement | null = document.querySelector("#bill-input");
        const peopleInput:HTMLInputElement | null = document.querySelector("#people-input");

        inputs.forEach((el) => {
            el.addEventListener("input", (e) => {
                enforceMaxLength(e, el, maxlength);
                calculate();
            })
        })
    })
    
</script>

<section class="input">
    <h3>Bill</h3>
    <h2><img src={IconDollar} alt="icon-dollar"><input type="number" placeholder="0" maxlength="16" id="bill-input" bind:value={bill}></h2>
    <h3>Select Tip %</h3>
    <ButtonPanel bind:tipPercent={tipPercent} bind:selected={buttonPanelSelection} calculate={calculate}></ButtonPanel>
    <h3>Number of People</h3>
    <h2><img src={IconPerson} alt="icon-person"><input type="number" placeholder="0" maxlength="16" id="people-input" bind:value={people}></h2>
</section>