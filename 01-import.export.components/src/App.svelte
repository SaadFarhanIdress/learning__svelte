<script>
  import Smiley from "./Smiley.svelte";
  let say = "hi";

  setTimeout(() => {
    say = "bye";
  }, 1000);
</script>

<div>
  Say {say}
</div>

<Smiley />

<style>
  div {
    color: red;
  }
</style>
