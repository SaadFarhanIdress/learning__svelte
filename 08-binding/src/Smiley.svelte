<script>
  export let happyScore = 1;
  export let size = 1;

  const faces = ["😐", "🙂", "😀", "😄", "😊", "😘"];
</script>

<div style="font-size: {size}em">{faces[happyScore]}</div>
