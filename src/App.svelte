<script>
  import Router from "svelte-spa-router";
  import Main from "./pages/Main.svelte";
  import "./css/style.css";

  const routes = {
    "/": Main,
  };
</script>

<Router {routes} />
