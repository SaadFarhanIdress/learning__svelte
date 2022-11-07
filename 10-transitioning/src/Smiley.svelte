<script>
  import { fade, slide } from "svelte/transition";
  import { sineIn } from "svelte/easing";

  export let happyScore = 0;
  export let size = 1;

  const faces = [
    "🤬",
    "😡",
    "😭",
    "🙁",
    "😕",
    "😐",
    "🙂",
    "😀",
    "😄",
    "😊",
    "😘",
  ];
  let visible = true;
  let duration = 400;
  let delay = 0;
  let status = "Waiting...";
</script>

<p>Animation status: {status}</p>
{#if visible}
  <div
    style="font-size: {size}em"
    in:slide={{ delay, duration, easing: sineIn }}
    out:fade={{ delay, duration, easing: sineIn }}
    on:introstart={() => (status = '"In" animation starts')}
    on:outrostart={() => (status = '"Out" animation starts')}
    on:introend={() => (status = '"In" animation ends')}
    on:outroend={() => (status = '"Out" animation ends')}
  >
    {faces[happyScore + 5]}
  </div>
{/if}

<div>
  Visible
  <input type="checkbox" bind:checked={visible} />
  <br />
  duration
  <input type="number" maxlength="5" bind:value={duration} />
  <br />
  delay
  <input type="number" maxlength="5" bind:value={delay} />
</div>
