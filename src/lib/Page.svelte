<script lang="ts">
  import {onMount} from "svelte";

  export let show: bool;
  export let index: number;

  let loading = true;

  let element;

  onMount(() => {
    element.setAttribute("index", index);
  })


  export function getElement() {
    return element;
  }
</script>

<div bind:this={element} class="bg-white w-[500px] h-[700px] min-h-[700px] my-4" class:animate-pulse={loading}>
  {#if show}

  {/if}
</div>