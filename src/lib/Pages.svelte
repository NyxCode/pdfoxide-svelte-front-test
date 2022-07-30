<script lang="ts">
  import Page from "./Page.svelte";
  import {onMount} from "svelte";

  const PRERENDER_MARGIN = "70%";

  let pages = [...Array(12).keys()].map(index => ({
    index,
    show: false,
    element: null
  }));
  let wrapper;
  let observer;

  onMount(() => {
    pages.forEach(page => page.element.getElement().setAttribute("index", page.index));

    observer = new IntersectionObserver((a, b) => {
      a.forEach(entry => {
        let index = parseInt(entry.target.getAttribute("index"));
        console.log(index);
        pages[index].show = entry.isIntersecting;
        pages = pages;
      });
    }, {root: wrapper, rootMargin: `${PRERENDER_MARGIN} 0%`});
    
    console.log(pages);
    pages.forEach(page => observer.observe(page.element.getElement()));

    let interval = setInterval(() => {
      console.log("visible", pages.filter(p => p.show).map(p => p.index))
    }, 500);

    return () => {
      clearInterval(interval);
      observer.disconnect();
    };
  });
</script>

<div bind:this={wrapper} class="pages-scrollbar flex flex-col items-center w-full overflow-auto">
  {#each pages as page, i}
    <Page index={i} bind:this={page.element} show={pages[i].show} />
  {/each}
</div>

<style>

</style>