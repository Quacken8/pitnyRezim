<script lang="ts">
  import Person from "./lib/Person.svelte";
  import Controls from "./lib/Controls.svelte";
</script>

<main class="container">

  <Person name="John Doe" />
  <Person name="Jane Doe" />
  <Person name="John Smith" />
  <Person name="Jane Smith" />
  <Controls/>

</main>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>