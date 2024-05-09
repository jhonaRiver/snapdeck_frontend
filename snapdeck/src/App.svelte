<script>
  import LogIn from "./LogIn.svelte";
  import LogOut from "./LogOut.svelte";
  import CardRecommendation from "./CardRecommendation.svelte";

  let isLoggedIn = false;

  function handleLogout() {
    isLoggedIn = false;
  }
</script>

<body>
  <main>
    <h1>Snap Deck</h1>
    {#if isLoggedIn}
      <LogOut bind:isLoggedIn />
      <CardRecommendation />
    {:else}
      <LogIn bind:isLoggedIn />
    {/if}
  </main>
</body>

<style>
  body {
    margin: 0;
    padding: 0;
    background-image: url("/build/images/galaxy.jpg");
    background-size: cover;
    background-position: center;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: whitesmoke;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: bold;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
