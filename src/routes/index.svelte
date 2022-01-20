<script>
  import { onMount } from "svelte";
  let name;
  const sizes = [100, 200, 300, 400, 500]
  const choice = (things) => things[Math.floor(Math.random() * things.length)];
  onMount(async () => {
    console.log("onMount");
    let response = await fetch("/.netlify/functions/name");
    ({ name } = await response.json());
  });
  const src = `https://picsum.photos/${choice(sizes)}/${choice(sizes)}`
</script>

<style>
  h1,
  figure {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  figure {
    margin: 0 0 1em 0;
  }

  img {
    width: 100%;
    max-width: 400px;
    margin: 0 0 1em 0;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }
</style>

<svelte:head>
  <title>Wait so you're here but not sure why?</title>
</svelte:head>

{#if name}
  <h1>{name}</h1>
  <figure>
    <img alt={name} src />
  </figure>
{:else}
  <p>Loading something awesome...</p>
{/if}
