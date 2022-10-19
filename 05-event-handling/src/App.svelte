<script>
  import Smiley from "./Smiley.svelte";
  import Container from "./Container.svelte";
  import Header from "./Header.svelte";
  import Button from "./Button.svelte";

  let say = false;
  let showHeader = false;

  setTimeout(() => {
    say = true;
    showHeader = false;
  }, 1000);
</script>

{#if showHeader}
  <Header />
{/if}

<Container>
  {#if say}
    <div>Hi!</div>
  {:else if !say}
    Not saying anything
  {/if}

  {#each [2, 1, 0] as index}
    <Smiley {index} size={index + 1} />
  {/each}

  <Button on:click={() => (showHeader = !showHeader)}>Show Header</Button>
</Container>

<style>
  div {
    color: red;
  }
  :global(*) {
    box-sizing: border-box;
  }
  :global(body, html) {
    margin: 0;
    height: 100vh;
    overflow: hidden;
  }
</style>
