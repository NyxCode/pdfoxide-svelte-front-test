<script lang="ts">
  import Page from "./Page.svelte";
  import {onMount} from "svelte";

  const PRERENDER_MARGIN = "30%";

  let pages = [...Array(12).keys()].map(index => ({
    index,
    show: false,
    element: null
  }));
  let wrapper;

  onMount(() => {
    pages.forEach(page => page.element.setAttribute("index", page.index));

    let observer = new IntersectionObserver((a, b) => {
      a.forEach(entry => {
        let index = parseInt(entry.target.getAttribute("index"));
        pages[index].show = entry.isIntersecting;
      });
    }, {root: wrapper, rootMargin: `${PRERENDER_MARGIN} 0%`});
    
    pages.forEach(page => observer.observe(page.element));

    return () => {
      observer.disconnect();
    };
  });
</script>

<div bind:this={wrapper} class="pages-scrollbar flex flex-col items-center w-full overflow-auto">
  {#each pages as page, i}
    <Page bind:page />
  {/each}
</div>

<style>

</style>