<script>
  export let isLoggedIn;
  let email = "";
  let password = "";
  let message = "";

  async function handleLogIn() {
    const response = await fetch("http://localhost:5000/login", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ email, password }),
    });
    const data = await response.json();
    if (response.ok) {
      message = "Login successful!";
      isLoggedIn = true;
    } else {
      message = data.error;
    }
  }
</script>

<h1>Login</h1>

<form on:submit|preventDefault={handleLogIn}>
  <div>
    <label for="email">Email:</label>
    <input type="email" id="email" bind:value={email} required />
  </div>
  <div>
    <label for="password">Password:</label>
    <input type="password" id="password" bind:value={password} required />
  </div>
  <button type="submit">Login</button>
</form>

<!-- TODO: Add basic auth -->

<style>
  label {
    color: whitesmoke;
  }

  h1 {
    color: whitesmoke;
    font-size: 3em;
    font-weight: bold;
  }
</style>
