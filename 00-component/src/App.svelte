<script>
  let say = "hi";

  setTimeout(() => {
    say = "bye";
  }, 1000);
</script>

<div>
  Say {say}
</div>

<style>
  div {
    color: red;
  }
  :global(div) {
    background: blue;
  }
</style>
