<script>
  import logo from "./assets/svelte.png";
  import Router from "svelte-spa-router";
  import { link } from "svelte-spa-router";

  // Import the list of routes
  import routes from "./routes";
  import { onMount } from "svelte";

  onMount(() => {
    const currentUrl = window.location.href;
    if (currentUrl.slice(-1) !== "/") {
      window.location.href = currentUrl + "/";
    }
  });
</script>

<main>
  <img src={logo} alt="Svelte Logo" />

  <!-- Navigation links -->
  <ul>
    <li><a href="/" use:link>Home</a></li>
    <li>
      <a href="/hello/svelte" use:link>Say hi!</a> (dynamically imported route)
    </li>
    <li>
      <a href="/wild/card" use:link>Wildcard route </a> (dynamically imported route,
      with a 5 seconds artificial delay)
    </li>
    <li><a href="/does/not/exist" use:link>Not found</a></li>
  </ul>

  <!-- Show the router -->
  <Router {routes} />
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }
</style>
