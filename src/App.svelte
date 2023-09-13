<script lang="ts">
    import Logo from './assets/logo.svg';
    import Input from './lib/Input.svelte';
    import Output from './lib/Output.svelte';

    let bill:number | null = null;
    let tipPercent:number | null = null;
    let people:number | null = null;

    let tipPerPerson:number = 0;
    let totalPerPerson:number = 0;

    let buttonPanelSelection:number | null = null;
    let outputExists:boolean = false;

    const reset:Function = () => {
        bill = null;
        tipPercent = null;
        people = null;

        totalPerPerson = 0;
        tipPerPerson = 0;

        buttonPanelSelection = null;

        outputExists = false;
    }

    const calculate = () => {
        console.log(bill)
        if((bill && bill !== 0) && tipPercent !== null && (people && people !== 0)) {        
            const tipTotal = Number((bill * (tipPercent / 100)).toFixed(2));
            const total = Number((bill + tipTotal).toFixed(2));

            tipPerPerson = tipTotal / people;
            totalPerPerson = total / people;

            outputExists = true;
        }
    }
</script>

<main>
    <h1><img src={Logo} alt="logo"></h1>
    <section class="container">
        <Input bind:bill={bill} bind:tipPercent={tipPercent} bind:people={people} calculate={calculate} bind:buttonPanelSelection={buttonPanelSelection}></Input>
        <Output tipPerPerson={tipPerPerson} totalPerPerson={totalPerPerson} outputExists={outputExists} reset={reset}></Output>
    </section>
</main>

<style>
</style>
