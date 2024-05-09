<script>
  export let isLoggedIn;

  async function handleLogout() {
    const response = await fetch("http://localhost:5000/logout", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
    });
    const data = await response.json();
    if (response.ok) {
      isLoggedIn = false;
    }
  }
</script>

<button class="logout-button" on:click={handleLogout}>Logout</button>

<style>
  .logout-button {
    position: absolute;
    top: 10px;
    right: 10px;
  }
</style>
