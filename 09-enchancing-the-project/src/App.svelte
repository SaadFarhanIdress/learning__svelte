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

  $: question = story[storyIndex];
  $: buttons = question.buttons;

  $: happyScore = 0;
  let storyIndex = 0;

  $: message = question.end ? finalMessage() : question.smileySays;
  $: if (happyScore < -4) message = "You're a monster!";
  $: if (happyScore > 0 && storyIndex === 3) showHeader = true;

  function finalMessage() {
    if (happyScore > 0) {
      return question.end.nice;
    } else if (happyScore < 0) {
      return question.end.neutral;
    } else {
      return question.end.mean;
    }
  }

  /**
   * @param {{ value: number | string; }} btn
   */
  function clickHandler(btn) {
    if (typeof btn.value === "string") {
      storyIndex = 0;
      happyScore = 0;
      showHeader = false;
    } else {
      storyIndex++;
      console.log(storyIndex);
      happyScore += btn.value;
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
  h1 {
    text-align: center;
    background: #ff3e00;
    font-size: 2em;
    padding: 0.3em 0.6em;
    color: white;
    border-radius: 50px;
  }
  input {
    margin: 1em;
    width: 250px;
    font-family: "Nunito", sans-serif;
    border: 0;
    outline: 0;
    background: transparent;
    border-bottom: 1px solid black;
    text-align: center;
    font-size: 2em;
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
