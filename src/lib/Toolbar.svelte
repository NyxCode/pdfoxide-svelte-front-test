<script lang="ts">
  import Menu from "svelte-material-icons/Menu.svelte";
  import DotsVertical from "svelte-material-icons/DotsVertical.svelte";
  import Download from "svelte-material-icons/Download.svelte";
  import Printer from "svelte-material-icons/Printer.svelte";
  import ToolbarButton from "./ToolbarButton.svelte";
  import ToolbarInput from "./ToolbarInput.svelte";
</script>

<div class="bg-zinc-800 text-white flex flex-row items-center px-3 py-2 justify-between">

  <div class="flex flex-row items-center gap-x-2">
    <ToolbarButton>
      <Menu/>
    </ToolbarButton>
    <span class="text-sm">FileName.pdf</span>
  </div>

  <div class="flex flex-row">
    <ToolbarInput value={12} />
    <span class="ml-1">/ 24</span>
  </div>

  <div class="flex flex-row gap-x-1">
    <ToolbarButton>
      <Download />
    </ToolbarButton>
    <ToolbarButton>
      <Printer />
    </ToolbarButton>
    <ToolbarButton>
      <DotsVertical />
    </ToolbarButton>
    
    
    
  </div>
</div>