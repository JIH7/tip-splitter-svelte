<script lang="ts">
    import ButtonPanel from "./ButtonPanel.svelte";
    import IconDollar from "../assets/icon-dollar.svg";
    import IconPerson from "../assets/icon-person.svg";

    import { onMount } from "svelte";

    const maxlength = 16;

    export let bill;
    export let tipPercent;
    export let people;

    const enforceMaxLength = ( e:Event , input:HTMLInputElement, length:number ) => {
        if (input.value.toString().length >= length) {
            e.preventDefault();
        }
    }

    onMount(() => {
        const inputs:NodeListOf<HTMLInputElement> = document.querySelectorAll("h2 > input[type=number]");
        
        inputs.forEach((el) => {
            el.addEventListener("keypress", (e) => {
                enforceMaxLength(e, el, maxlength);
            })
        })
    })
    
</script>

<section class="input">
    <h3>Bill</h3>
    <h2><img src={IconDollar} alt="icon-dollar"><input type="number" placeholder="0" maxlength="16"></h2>
    <h3>Select Tip %</h3>
    <ButtonPanel></ButtonPanel>
    <h3>Number of People</h3>
    <h2><img src={IconPerson} alt="icon-person"><input type="number" placeholder="0" maxlength="16"></h2>
</section>