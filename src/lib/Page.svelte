<script lang="ts">
  import {onMount} from "svelte";

  export let page;
  let loading = true;
</script>

<div bind:this={page.element} 
     class="bg-white w-[500px] h-[700px] min-h-[700px] my-4 drop-shadow" 
    class:animate-pulse={loading}>
  {#if page.show}
    Shown!
  {/if}
</div>