<script>
  export let prevPage;
  export let nextPage;
  export let page;
</script>

<button on:click={() => prevPage()} disabled={page === 1}
  ><i class="fa-solid fa-arrow-left" /></button
>
<h2 class="page">{page}</h2>

<button on:click={() => nextPage()} disabled={page === 42}
  ><i class="fa-solid fa-arrow-right" /></button
>
