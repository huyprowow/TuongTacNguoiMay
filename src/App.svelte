<script>
  import Login from "./routes/Login.svelte";

  import Home from "./routes/home/Home.svelte";
  import { Router, Route } from "svelte-routing";
  import Product from "./routes/product/Product.svelte";
  import Cart from "./routes/cart/Cart.svelte";
  import Invoice from "./routes/invoice/Invoice.svelte";
</script>

<Router>
  <Route component={Home} />
  <Route path="/login" component={Login} />
  <Route path="/product" component={Product} />
  <Route path="/cart" component={Cart} />
  <Route path="/invoice" component={Invoice} />
</Router>

<style>
  :root::-webkit-scrollbar {
    display: none;
  }
</style>
