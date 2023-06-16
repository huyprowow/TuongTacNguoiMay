<script>
  import {
    Navbar,
    NavbarBrand,
    Form,
    Input,
    Nav,
    NavItem,
    NavLink,
    ButtonDropdown,
    Button,
    DropdownItem,
    DropdownMenu,
    DropdownToggle,
  } from "sveltestrap";
  import {push, pop, replace} from 'svelte-spa-router'
  let username = localStorage.getItem("username");
  function go(location) {
    if (location == "/logout") localStorage.removeItem("username");
    push(location);
  }
</script>

<Navbar id="home_nav" expand="md" class="ps-5" light color="light">
  <NavbarBrand href="/TuongTacNguoiMay/">Logo</NavbarBrand>
  <Form style="position: relative;">
    <Input
      type="search"
      class="form-control-sm has-feedback"
      name="search"
      id="search"
      placeholder="search"
      style="width: 300px;"
    />
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="16"
      height="16"
      fill="currentColor"
      class="bi bi-search form-control-feedback"
      viewBox="0 0 16 16"
      style="position: absolute; top: 8; right: 5;"
    >
      <path
        d="M11.742 10.344a6.5 6.5 0 1 0-1.397 1.398h-.001c.03.04.062.078.098.115l3.85 3.85a1 1 0 0 0 1.415-1.414l-3.85-3.85a1.007 1.007 0 0 0-.115-.1zM12 6.5a5.5 5.5 0 1 1-11 0 5.5 5.5 0 0 1 11 0z"
      />
    </svg>
  </Form>

  <Nav class="flex-grow-1 justify-content-end">
    <ul class="list-unstyled d-flex flex-column align-items-center">
      <li>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="16"
          height="16"
          fill="currentColor"
          class="bi bi-telephone"
          viewBox="0 0 16 16"
        >
          <path
            d="M3.654 1.328a.678.678 0 0 0-1.015-.063L1.605 2.3c-.483.484-.661 1.169-.45 1.77a17.568 17.568 0 0 0 4.168 6.608 17.569 17.569 0 0 0 6.608 4.168c.601.211 1.286.033 1.77-.45l1.034-1.034a.678.678 0 0 0-.063-1.015l-2.307-1.794a.678.678 0 0 0-.58-.122l-2.19.547a1.745 1.745 0 0 1-1.657-.459L5.482 8.062a1.745 1.745 0 0 1-.46-1.657l.548-2.19a.678.678 0 0 0-.122-.58L3.654 1.328zM1.884.511a1.745 1.745 0 0 1 2.612.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z"
          />
        </svg>
        HOTLINE: 0395534600
      </li>
      <li>Địa chỉ: số xx phường xx quận xx TP.xx</li>
    </ul>

    <NavItem
      class="d-flex align-items-center  justify-content-center"
      style="min-width: 100px;"
    >
      {#if username === "huy"}
        <Button
          on:click={() => go("/cart")}
          color="light"
          class="d-flex align-items-center"
          style="border-radius: 50%; width: 40px; height: 40px;"
          ><svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-cart"
            viewBox="0 0 16 16"
          >
            <path
              d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM3.102 4l1.313 7h8.17l1.313-7H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"
            />
          </svg></Button
        >
        <ButtonDropdown>
          <DropdownToggle
            color="light"
            class="d-flex align-items-center"
            style="border-radius: 50%; width: 40px; height: 40px; "
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              width="32"
              height="32"
              fill="currentColor"
              class="bi bi-person-circle"
              viewBox="0 0 16 16"
            >
              <path d="M11 6a3 3 0 1 1-6 0 3 3 0 0 1 6 0z" />
              <path
                fill-rule="evenodd"
                d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8zm8-7a7 7 0 0 0-5.468 11.37C3.242 11.226 4.805 10 8 10s4.757 1.225 5.468 2.37A7 7 0 0 0 8 1z"
              />
            </svg>
          </DropdownToggle>
          <DropdownMenu>
            <DropdownItem on:click={() => go("/cart")}>Giỏ hàng</DropdownItem>
            <DropdownItem on:click={() => go("/invoice")}>Đơn mua</DropdownItem>
            <DropdownItem on:click={() => go("/login")}>Đăng xuất</DropdownItem>
          </DropdownMenu>
        </ButtonDropdown>
      {:else}
        <p on:click={() => go('/login')} on:keydown={(e) => {if (e.key === 'Enter') go('/login')}} style="color:black;">Đăng nhập/Đăng kí</p>
      {/if}
    </NavItem>
  </Nav>
</Navbar>
