<script>
  import "../node_modules/materialize-css/dist/css/materialize.min.css";
  import "../node_modules/materialize-css/dist/js/materialize.min.js";

  import { Router, Route } from "svelte-routing";

  import Navbar from "./layout/navbar.svelte";
  import Home from "./pages/home.svelte";
	 import About from './pages/about.svelte';	

</script>

<style>

</style>

<main />
<Router>
  <Navbar />
  <div class="container">
    <Route path="/" component={Home} />
    <Route path="/about" component={About} />
  </div>
</Router>
