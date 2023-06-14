<script>
  import Login from "./routes/Login.svelte";

  import Home from "./routes/home/Home.svelte";
  import { Router, Route } from "svelte-routing";
</script>

<Router>
  <Route component={Home} />
  <Route path="/login" component={Login} />
</Router>

<style>
  :root::-webkit-scrollbar {
    display: none;
  }
</style>
