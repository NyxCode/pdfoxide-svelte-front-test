<script lang="ts">
  import Menu from "svelte-material-icons/Menu.svelte";
  import DotsVertical from "svelte-material-icons/DotsVertical.svelte";
  import Download from "svelte-material-icons/Download.svelte";
  import Printer from "svelte-material-icons/Printer.svelte";
  import ToolbarButton from "./ToolbarButton.svelte";
  import ToolbarInput from "./ToolbarInput.svelte";


  export let drawer: bool;
</script>

<div class="bg-zinc-800 text-white flex flex-row items-center px-3 py-3 justify-between drop-shadow-lg">

  <div class="flex flex-row items-center gap-x-2">
    <ToolbarButton on:click={() => drawer = !drawer}>
      <Menu size="1.5em" />
    </ToolbarButton>
    <span class="text-sm">FileName.pdf</span>
  </div>

  <div class="flex flex-row text-sm">
    <ToolbarInput value={12} />
    <span class="ml-1">/ 24</span>
  </div>

  <div class="flex flex-row gap-x-1">
    <ToolbarButton>
      <Download size="1.5em" />
    </ToolbarButton>
    <ToolbarButton>
      <Printer size="1.5em" />
    </ToolbarButton>
    <ToolbarButton>
      <DotsVertical size="1.5em" />
    </ToolbarButton>
  </div>
</div>