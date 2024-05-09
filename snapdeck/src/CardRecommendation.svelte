<script>
  import CardModal from "./CardModal.svelte";

  let cardName = "";
  let recommendedCards = [];
  let selectedCard = null;

  async function getRecommendations() {
    const response = await fetch(
      `http://localhost:5000/recommendations?cardName=${cardName}`
    );
    recommendedCards = await response.json();
  }

  async function selectCard(cardName) {
    const response = await fetch(
      `http://localhost:5000/card?cardName=${cardName}`
    );
    const data = await response.json();
    selectedCard = data;
  }

  async function handleSubmit(event) {
    event.preventDefault();
    await getRecommendations();
  }
</script>

<main>
  <form on:submit={handleSubmit}>
    <input bind:value={cardName} placeholder="Enter card name" />
    <button type="submit">Get Recommendations</button>
  </form>

  {#if recommendedCards.length > 0}
    <h2>Recommended Deck:</h2>
    <div class="grid">
      {#each recommendedCards as card (card)}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <img src={card.img} alt="Card" on:click={() => selectCard(card.name)} />
      {/each}
    </div>
  {/if}

  <CardModal bind:card={selectedCard} />
</main>

<style>
  .grid {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-template-rows: repeat(2, 1fr);
    gap: 10px;
  }
  img {
    width: 100%;
    height: auto;
  }
  h2 {
    color: whitesmoke;
    font-size: 2em;
    font-weight: bold;
  }
</style>
