<script>
  import { onMount } from "svelte";
  let name;
  onMount(async () => {
    console.log("onMount");
    let response = await fetch("/.netlify/functions/name");
    console.log();
    ({ name } = await response.json());
  });
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
  <title>Sapper project template</title>
</svelte:head>

{#if name}
  <h1>{name}</h1>
  <figure>
    <img alt="Success Kid" src="successkid.jpg" />
  </figure>
{:else}
  <p>Loading...</p>
{/if}
