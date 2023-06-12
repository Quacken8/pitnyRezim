<script lang="ts">
    import Fa from "svelte-fa";
    import { faDroplet as solidDroplet } from "@fortawesome/free-solid-svg-icons";
    import { faDropletSlash as regularDroplet } from "@fortawesome/free-solid-svg-icons";

    export let name = "John Doe";
    export let currentHidration = 0;
    const maxHidration = 10;
    const minHidration = 0;

    const waterHidration = 3;
    const coffeeHidration = 1;

    function drinkWater() {
        currentHidration = Math.min(
            currentHidration + waterHidration,
            maxHidration
        );
    }
    function drinkCoffee() {
        currentHidration = Math.min(
            currentHidration + coffeeHidration,
            maxHidration
        );
    }
    function loseHidration() {
        currentHidration = Math.max(currentHidration - 1, minHidration);
    }
    function range(start, end) {
        return Array.from({ length: end - start }, (_, i) => start + i);
    }
</script>

<div class="person">
    <div class="name">
        {name}
    </div>
    <div class="bar">
        {#each range(minHidration, currentHidration) as _}
            <div class="icon">
                <Fa icon={solidDroplet} />
            </div>
        {/each}
        {#each range(currentHidration, maxHidration) as _}
            <div class="icon">
                <Fa class="icon" icon={regularDroplet} />
            </div>
        {/each}
    </div>
    <button class="water" on:click={drinkWater}> Water </button>
    <button class="coffee" on:click={drinkCoffee}> Coffee </button>
</div>

<style lang="scss">
    .icon {
        width: 1em;
        margin: 0 0.1em;
        display:flex;
        align-items: center;
        justify-content: center;
    }
    .person {
        display: grid;
        grid-template-columns: 2fr 3fr 1fr 1fr;
        grid-template-rows: 1fr;
        grid-template-areas: "name bar water coffee";
    }
    @mixin centered {
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .name {
        grid-area: name;
        @include centered;
    }
    .bar {
        grid-area: bar;
        @include centered;
    }
    .water {
        grid-area: water;
        @include centered;
    }
    .coffee {
        grid-area: coffee;
        @include centered;
    }
</style>
