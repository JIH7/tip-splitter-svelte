<script>
    import ButtonPanel from "./ButtonPanel.svelte";
    import IconDollar from "../assets/icon-dollar.svg";
    import IconPerson from "../assets/icon-person.svg";
</script>

<section>
    <h3>Bill</h3>
    <h2><img src={IconDollar} alt="icon-dollar"><input type="number" placeholder="0"></h2>
    <h3>Select Tip %</h3>
    <ButtonPanel></ButtonPanel>
    <h3>Number of People</h3>
    <h2><img src={IconPerson} alt="icon-person"><input type="number" placeholder="0"></h2>
</section>