<script lang="ts">
    import Fa from "svelte-fa";
    import { faUserPlus as solidUserPlus } from "@fortawesome/free-solid-svg-icons";
</script>

<div class="controls">
    <div class="newPerson">
        <input type="text" placeholder="New Person" />
        <button class="addUser">
            <Fa icon={solidUserPlus} />
        </button>
    </div>
    <div class="non" />
    <div class="waterValue">Water</div>
    <div class="coffeeValue">Coffee</div>
</div>

<style lang="scss">
    .controls {
        display: grid;
        grid-template-columns: 2fr 3fr 1fr 1fr;
        grid-template-rows: 1fr;
        grid-template-areas: "newPerson non waterValue coffeeValue";
    }

    @mixin centered {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .newPerson {
        grid-area: newPerson;
        @include centered;
    }

    .non {
        grid-area: non;
        @include centered;
    }

    .waterValue {
        grid-area: waterValue;
        @include centered;
    }

    .coffeeValue {
        grid-area: coffeeValue;
        @include centered;
    }

</style>
