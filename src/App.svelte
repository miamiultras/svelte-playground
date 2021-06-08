<script>
  import { flip } from "svelte/animate";
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  let isDescending = false;
  let index = 0;
  let length = 3;
  let arr;
  $: {
    arr = [...Array(length).keys()].map((x) => index + x);
    if (isDescending) arr.reverse();
  }
</script>

<main class="app">
  <h1>Characters of Stan Lee</h1>
  <div class="controls">
    <label>
      Show
      <input type="number" bind:value={length} min="0" />
    </label>
    <div>
      <input id="ascending" type="checkbox" bind:checked={isDescending} />
      <label for="ascending">Descending?</label>
    </div>

    <Button label={index} on:click={() => index++} />
  </div>
  {#each arr as id (id)}
    <div animate:flip={{ duration: 1000 }}>
      <Card index={id} />
    </div>
  {:else}
    <img
      alt="snap"
      src="https://i.insider.com/5ae3327e19ee8657008b45f6?width=750&format=jpeg&auto=webp"
    />
  {/each}
</main>

<style>
  .app {
    margin: 0 auto;
    transition: all 0.5s ease;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  .controls {
    display: flex;
    width: 600px;
    align-items: center;
    justify-content: space-between;
  }

  label {
    display: inline;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
