<script>
  import Character from "./lib/Character.svelte";
  import Heading from "./lib/Heading.svelte";
  import Buttons from "./lib/Buttons.svelte";
  let characters = [];
  let page = 1;

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

<main>
  <Heading />
  <div class="btns">
    <Buttons {prevPage} {page} {nextPage} />
  </div>
  <div class="container">
    <div class="grid">
      {#each characters as character}
        <Character {character} />
      {/each}
    </div>
  </div>
</main>
