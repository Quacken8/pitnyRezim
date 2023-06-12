<script lang="ts">
  import Person from "./lib/Person.svelte";
</script>

<main class="container">

  <Person name="John Doe" />
  <Person name="Jane Doe" />
  <Person name="John Smith" />
  <Person name="Jane Smith" />

</main>

<style>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>