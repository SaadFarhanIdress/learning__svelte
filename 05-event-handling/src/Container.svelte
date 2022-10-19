<div class="Container">
  <slot />
</div>

<style>
  .Container {
    height: 100vh;
    width: 100vw;
    font-family: "Segoe UI", sans-serif;
    border: solid black 20px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
