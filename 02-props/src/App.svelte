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

<Smiley size={3} />
<Smiley size={4} index={1} />
<Smiley size={5} index={2} />

<style>
  div {
    color: red;
  }
</style>
