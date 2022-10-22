<script>
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
</script>

<div style="font-size: {size}em">{faces[happyScore + 5]}</div>
