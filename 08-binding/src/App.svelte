<script>
  import Smiley from "./Smiley.svelte";
  import Container from "./Container.svelte";
  import Header from "./Header.svelte";
  import Buttons from "./Buttons.svelte";

  import story from "./story";

  let say = false;
  let showHeader = false;

  setTimeout(() => {
    say = true;
    showHeader = false;
  }, 1000);

  $: buttons = story[storyIndex].buttons;

  let happyScore = 0;
  let storyIndex = 0;

  $: message = story[storyIndex].smileySays;
  $: if (happyScore < -4) message = "You're a monster!";

  /**
   * @param {{ text: string; value: number; }} story
   */
  function clickHandler(story) {
    if (story.text !== "Reset") {
      storyIndex++;
      happyScore++;
    } else {
      storyIndex = 0;
      happyScore = 0;
    }
  }

  let name = "Human";
</script>

{#if showHeader}
  <Header />
{/if}

<Container>
  <input type="text" bind:value={name} />

  {#if say}
    <h1>{name}, {message}</h1>
  {:else if !say}
    Not saying anything
  {/if}

  <Smiley {happyScore} size={storyIndex + 1} />

  <Buttons
    on:clickHeaderToggler={(e) => {
      showHeader = e.detail;
    }}
    on:clickStory={(e) => {
      clickHandler(e.detail);
    }}
    {buttons}
  />
</Container>

<style>
  :global(*) {
    box-sizing: border-box;
  }
  :global(body, html) {
    margin: 0;
    height: 100vh;
    overflow: hidden;
  }
</style>
