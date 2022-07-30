<script lang="ts">
  export let value: any;
</script>


<input type="number" class="mr-0 w-8 bg-zinc-900 rounded text-right pr-[3px]" inputmode="numeric" pattern="[0-9]*" bind:value>

<style>
  input[type="number"]::-webkit-outer-spin-button,
  input[type="number"]::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
  }
  input[type="number"] {
      -moz-appearance: textfield;
  }
</style>