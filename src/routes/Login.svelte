<script>
  import { Nav, NavItem, Button } from "sveltestrap";
  import SignUp from "../component/signUp.svelte";
  import SignIn from "../component/signIn.svelte";
  export let signup = false;
  function handleClick(_signup) {
    signup = _signup;
    console.log(signup);
  }
</script>

<main style="height:100vh;">
  <Nav style="display:flex;flex-direction:row-reverse">
    <NavItem>
      <Button
        color={signup ? "light" : "dark"}
        style="border-radius: 0px 0px 0px 0px;"
        on:click={() => handleClick(false)}>Đăng kí</Button
      >
    </NavItem>
    <NavItem>
      <Button
        color={!signup ? "light" : "dark"}
        style="border-radius: 0px 0px 0px 0px;"
        on:click={() => handleClick(true)}>Đăng nhập</Button
      >
    </NavItem>
  </Nav>
  {#if !signup}
    <SignUp />
  {:else}
    <SignIn />
  {/if}
</main>
