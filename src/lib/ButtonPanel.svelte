<script lang="ts">
    import { onMount } from "svelte";

    let selected:number | null = null;

    onMount(() => {
        const percentInput:HTMLInputElement | null = document.querySelector(".button-panel input[type=number]");

        // Handle inputs larger than 100
        percentInput?.addEventListener("keypress", (e) => {
            if(Number(percentInput.value) >= 100) {
                e.preventDefault();
                percentInput.value = "100";
            }
        })

        percentInput?.addEventListener("keyup", (e) => {
            if(Number(percentInput.value) > 100) {
                percentInput.value = "100";
            }
        })

        // Button event listeners
        const buttons:NodeListOf<HTMLElement> = document.querySelectorAll(".button-panel > *")

        buttons.forEach((button, i) => {
            const key = i;
            button.addEventListener("click", () => {
                selected = key;
            })
        })
    })
</script>

<div class="button-panel">
    <button class={selected === 0 ? "selected" : ""}>5%</button>
    <button class={selected === 1 ? "selected" : ""}>10%</button>
    <button class={selected === 2 ? "selected" : ""}>15%</button>
    <button class={selected === 3 ? "selected" : ""}>25%</button>
    <button class={selected === 4 ? "selected" : ""}>50%</button>
    <input class={selected === 5 ? "selected" : ""} type="number" placeholder="Custom">
</div>