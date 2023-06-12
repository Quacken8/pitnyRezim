<script lang="ts">
  import Fa from "svelte-fa";
  import { faUserPlus as solidUserPlus } from "@fortawesome/free-solid-svg-icons";
  import Person from "./lib/Person.svelte";
  import Controls from "./lib/Controls.svelte";

  let people = [{ id: -1, name: "John Doe" }];

  let newName: string = "";

  let currentId = 0;

  function addPerson(name: string) {
    people = [...people, { id: currentId, name: name }];
    currentId++;
  }

  function clearInput() {
    const input = document.querySelector("input");
    input.value = "";
  }

  function onPres() {
    if (newName === "") {
      return;
    }
    addPerson(newName);
    clearInput();
  }

  function handleRemovePerson(id) {
    people = people.filter((person) => person.id !== id);
  }
</script>

<main class="container">
  {#each people as person}
    <Person name={person.name} id={person.id} on:remove={ _ => handleRemovePerson(person.id)} />
  {/each}
  <Controls />

  <div class="controls">
    <div class="newPerson">
      <input type="text" placeholder="New Person" bind:value={newName} />
      <button class="addUser" on:click={onPres}>
        <Fa icon={solidUserPlus} />
      </button>
    </div>
  </div>
</main>

<style lang="scss">
  @mixin centered {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .newPerson {
    grid-area: newPerson;
    @include centered;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
