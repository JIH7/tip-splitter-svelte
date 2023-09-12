<script lang="ts">
    import Logo from './assets/logo.svg';
    import Input from './lib/Input.svelte';
    import Output from './lib/Output.svelte';

    let bill:number = 0;
    let tipPercent:number = 0;
    let people:number = 0;

    let tipPerPerson:number = 0;
    let totalPerPerson:number = 0;

    const calculate = () => {
        const tipTotal = Number((bill / tipPercent).toFixed(2));
        const total = Number((bill + tipTotal).toFixed(2));

        tipPerPerson = tipTotal / people;
        totalPerPerson = total / people;
    }
</script>

<main>
    <h1><img src={Logo} alt="logo"></h1>
    <section class="container">
        <Input bill={bill} tipPercent={tipPercent} people={people}></Input>
        <Output></Output>
    </section>
</main>

<style>
</style>
