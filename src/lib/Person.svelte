<script lang="ts">
    export let name = "John Doe";
    export let hidration = 0;
    const maxHidration = 10;
    const minHidration = 0;

    const waterHidration = 3;
    const coffeeHidration = 1;

    function drinkWater() {
        hidration = Math.min(hidration + waterHidration, maxHidration);
    }
    function drinkCoffee() {
        hidration = Math.min(hidration + coffeeHidration, maxHidration);
    }
    function loseHidration() {
        hidration = Math.max(hidration - 1, minHidration);
    }
</script>

<div class="person">
    <div class="name">
        {name}
    </div>
    <div class="bar">
        currently at {hidration}
    </div>
    <button class="water" on:click={drinkWater}>
        Water
    </button>
    <button class="coffee" on:click={drinkCoffee}>
        Coffee
    </button>
</div>

<style lang="scss">
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
