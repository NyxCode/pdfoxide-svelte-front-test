<script lang="ts">
  import Toolbar from "./Toolbar.svelte";
  import Drawer from "./Drawer.svelte";
  import { quintOut } from "svelte/easing";
  import Pages from "./Pages.svelte";
  import Page from "./Page.svelte";

  const DRAWER_WIDTH = 26;
  const slide = (node, params) => ({
    delay: 0,
    duration: 200,
    easing: quintOut,
    css: (t, u) => `margin-left: -${u * DRAWER_WIDTH}em`
  });

  let drawer = false;
</script>

<div class="h-full w-full bg-zinc-700 flex flex-col max-h-full">
  <Toolbar bind:drawer />
  <div class="flex flex-row transition-all overflow-hidden">
    {#if drawer}
      <div transition:slide style="width: {DRAWER_WIDTH}em">
        <Drawer />
      </div>
    {/if}

    <Pages />

  </div>
</div>