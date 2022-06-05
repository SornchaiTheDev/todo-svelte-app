<script>
  export let style = "";
</script>

<div class="card" {style} on:click>
  <slot />
</div>

<style>
  .card {
    background: #fff;
    padding: 10px;
    border-radius: 5px;
  }
</style>
