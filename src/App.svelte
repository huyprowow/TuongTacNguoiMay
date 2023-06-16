<script>
  import Login from "./routes/Login.svelte";

  import Home from "./routes/home/Home.svelte";
  import Router, { location, link } from "svelte-spa-router";
  // import { Router, Route } from "svelte-routing";
  import Product from "./routes/product/Product.svelte";
  import Cart from "./routes/cart/Cart.svelte";
  import Invoice from "./routes/invoice/Invoice.svelte";
</script>

<Router
  routes={{
    "/": Home,
    "/login": Login,
    "/product": Product,
    "/cart": Cart,
    "/invoice": Invoice,
  }}
/>

<style>
  :root::-webkit-scrollbar {
    display: none;
  }
</style>
