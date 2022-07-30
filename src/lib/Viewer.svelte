<script lang="ts">
  import Toolbar from "./Toolbar.svelte";
  import Drawer from "./Drawer.svelte";
  import { quintOut } from "svelte/easing";

  const DRAWER_WIDTH = 26;


  function slide(node, params) {
		return {
			delay: 0,
			duration: 200,
			easing: quintOut,
			css: (t, u) => `margin-left: -${u * DRAWER_WIDTH}em`
		};
	}

  let drawer = true;
  $: console.log(drawer);
</script>

<div class="h-full w-full bg-zinc-700 flex flex-col">
  <Toolbar bind:drawer />
  <div class="flex flex-row h-full transition-all">
    {#if drawer}
      <div transition:slide style="width: {DRAWER_WIDTH}em">
        <Drawer />
      </div>
    {/if}

    <div class="text-center w-full mt-auto mb-auto text-white text-4xl">
    Content
    </div>
  </div>

</div>