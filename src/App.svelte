<script>
  import Character from "./lib/Character.svelte";
  let characters = [];
  let page = 0;

  async function loadCharacters() {
    const response = await fetch(
      `https://rickandmortyapi.com/api/character?page=${page}`
    );
    const data = await response.json();
    characters = data.results;
  }
  loadCharacters();

  function nextPage() {
    page++;
    loadCharacters();
  }

  function prevPage() {
    page--;
    loadCharacters();
  }
</script>

<h1 class="heading">Rick and Morty Svelte</h1>
<div>
  <button on:click={() => prevPage()} disabled={page === 1}>Voltar</button>
  <button on:click={() => nextPage()}>Próximo</button>
</div>

<div class="container">
  <div class="grid">
    {#each characters as character}
      <Character {character} />
    {/each}
  </div>
</div>
