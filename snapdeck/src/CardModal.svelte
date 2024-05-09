<script>
  export let card = null;

  console.log("Card object:", card);
</script>

{#if card}
  <div class="modal">
    <div class="modal-content">
      <img
        src={card.img}
        alt="Card"
        on:error={() => console.error("Image load failed")}
      />
      <p>{card.ability}</p>
      <button on:click={() => (card = null)}>X</button>
    </div>
  </div>
{/if}

<style>
  .modal {
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .modal-content {
    position: relative;
    box-sizing: border-box;
    background-color: rgba(0, 0, 0, 0.8);
    padding: 20px;
    border: 1px solid #888;
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 90%;
    color: whitesmoke;
    font-weight: bold;
    font-size: 20px;
  }
  .modal-content img {
    width: auto;
    height: 70vh;
  }
  .modal-content button {
    position: absolute;
    top: 10px;
    right: 10px;
    background-color: red;
    color: whitesmoke;
    border: none;
    width: 25px;
    height: 25px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
  }
</style>
