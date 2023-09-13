<script lang="ts">
    export let tipPerPerson:number;
    export let totalPerPerson:number;
    export let outputExists:boolean = false;
    export let reset:Function;

    const handleClick = () => {
        reset();
    }
</script>

<section class="output">
    <div>
        <div>
            <h3>Tip Amount</h3>
            <p>/ person</p>
        </div>
        <h2>${tipPerPerson.toFixed(2)}</h2>
    </div>
    <div>
        <div>
            <h3>Total</h3>
            <p>/ person</p>
        </div>
        <h2>${totalPerPerson.toFixed(2)}</h2>
    </div>
    <button class={outputExists ? "active" : ""} on:click={handleClick}>RESET</button>
</section>