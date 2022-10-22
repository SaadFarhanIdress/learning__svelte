<script>
  import Smiley from "./Smiley.svelte";
  import Container from "./Container.svelte";
  import Header from "./Header.svelte";
  import Buttons from "./Buttons.svelte";

  let say = false;
  let showHeader = false;

  setTimeout(() => {
    say = true;
    showHeader = false;
  }, 1000);

  const buttons = [
    { value: 1, text: "ummmmmm......" },
    { value: 2, text: "I sure do!" },
    { value: -2, text: "gross!" },
  ];
  let score = 0;
</script>

{#if showHeader}
  <Header />
{/if}

<Container>
  {#if say}
    <div>Hi! {score}</div>
  {:else if !say}
    Not saying anything
  {/if}

  {#each [2, 1, 0] as index}
    <Smiley {index} size={index + 1} />
  {/each}

  <Buttons
    on:click={(e) => {
      if (e.detail.value) {
        score += e.detail.value;
      } else showHeader = e.detail;
    }}
    {buttons}
  />
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
