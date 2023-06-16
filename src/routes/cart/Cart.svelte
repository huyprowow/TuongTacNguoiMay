<script>
  import {
    Container,
    Breadcrumb,
    BreadcrumbItem,
    Button,
    Row,
    Col,
    InputGroup,
    InputGroupText,
    Input,
    Modal,
    ModalBody,
    ModalHeader,
    ModalFooter,
  } from "sveltestrap";
  import Header from "../../component/Header.svelte";
  import Footer from "../../component/Footer.svelte";
  import cartImport from "../../mocks/cart/cart.json";
  import { push } from "svelte-spa-router";
  function goto(path) {
    push(path);
  }
  // increase quantity ,decrease quantity delete item and total price
  let total = 0;
  let quantity = 1;
  let carts = cartImport;
  carts = carts.map((cart) => {
    total += cart.price;
    return cart;
  });
  function increaseQuantity() {
    quantity++;
    total += carts[0].price;
  }
  function decreaseQuantity() {
    if (quantity > 1) {
      quantity--;
      total -= carts[0].price;
    }
  }
  let idDel = cartImport[0].id;
  function deleteItem(id) {
    carts = carts.filter((cart) => cart.id != id);
    carts = [];
    toggle();
  }
  let open = false;
  let openPay = false;
  const toggle = (id) => {
    if (id) {
      idDel = id;
    }
    open = !open;
  };
  const togglePay = () => {
    openPay = !openPay;
  };
  let openSuccess = false;
  const toggleSuccess = () => {
    openSuccess = !openSuccess;
  };
  const pay = () => {
    togglePay();
    toggleSuccess();
    carts = [];
  };
  function formatPrice(price) {
    return price.toLocaleString("it-IT", {
      style: "currency",
      currency: "EUR",
    });
  }
</script>

<Container fluid class="p-0">
  <Header />
  <Breadcrumb class="px-5 pt-2" style="border-bottom:1px solid lightgray">
    <BreadcrumbItem>
      <a class="text-black-50 text-decoration-none" href="/TuongTacNguoiMay/"
        >Trang Chủ</a
      >
    </BreadcrumbItem>
    <BreadcrumbItem active>Đơn mua</BreadcrumbItem>
  </Breadcrumb>

  <Container class="text-center p-5" fluid>
    {#if carts.length > 0}
      {#each carts as cart}
        <Row>
          <Col class="d-flex flex-grow-1 gap-3">
            <img src={cart.image} alt="" srcset="" width="200" height="100" />
            <div>
              <h3>{cart.name}</h3>
              <p>{cart.desc}</p>
              <span
                class="text-decoration-underline text-danger"
                on:click={toggle}>Xóa</span
              >
            </div>
            <div>
              <span style="font-size: x-large;">{formatPrice(total)}</span>
              <InputGroup>
                <InputGroupText class="p-0 m-0">
                  <Button color="light" on:click={decreaseQuantity}>-</Button>
                </InputGroupText>
                <Input value={quantity} style="width:50px;" />
                <InputGroupText>
                  <Button
                    color="light"
                    class="p-0 m-0"
                    on:click={increaseQuantity}>+</Button
                  >
                </InputGroupText>
              </InputGroup>
            </div>
          </Col>
          <Col class="d-flex flex-column" style="max-width: 300px;">
            <div
              class="d-flex justify-content-between"
              style="font-size: larger;"
            >
              <b>Thành tiền: </b><span>{formatPrice(total)}</span>
            </div>
            <Button color="danger" class="my-2" on:click={togglePay}
              >Thanh toán ngay</Button
            >
            <Button
              color="light"
              class="border-1 border-black"
              on:click={function () {
                window.location.href = "/TuongTacNguoiMay/";
              }}>Tiếp tục mua hàng</Button
            >
          </Col>
        </Row>
      {/each}
    {:else}
      <Button color="secondary" style="border-radius: 50%;">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="40"
          height="50"
          fill="currentColor"
          class="bi bi-cart"
          viewBox="0 0 16 16"
        >
          <path
            d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM3.102 4l1.313 7h8.17l1.313-7H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"
          />
        </svg>
      </Button>
      <p class="text-center">Giỏ hàng của bạn đang trống</p>
      <a
        href="/TuongTacNguoiMay/"
        class="btn btn-danger"
        on:click={() => goto("/")}>Mua ngay</a
      >
    {/if}
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Xóa sản phẩm</ModalHeader>
      <ModalBody class="text-center">Xóa sản phẩm này khỏi giỏ hàng?</ModalBody>
      <ModalFooter class="d-flex justify-content-evenly">
        <Button color="light" class="border-1 border-black" on:click={toggle}
          >Hủy</Button
        >
        <Button color="danger" on:click={() => deleteItem(idDel)}>Xóa</Button>
      </ModalFooter>
    </Modal>
    <Modal isOpen={openPay} toggle={togglePay}>
      <ModalBody class="text-center"
        >Bạn có chắc chắn muốn thanh toán đơn hàng này không?</ModalBody
      >
      <ModalFooter class="d-flex justify-content-evenly">
        <Button color="light" class="border-1 border-black" on:click={togglePay}
          >Hủy</Button
        >
        <Button color="danger" on:click={pay}>Thanh toán</Button>
      </ModalFooter>
    </Modal>
    <Modal isOpen={openSuccess} toggle={toggleSuccess}>
      <ModalBody class="text-center">Thanh toán thành công!!</ModalBody>
      <ModalFooter class="d-flex justify-content-evenly">
        <Button
          color="light"
          class="border-1 border-black"
          on:click={() => {
            window.location.href = "/TuongTacNguoiMay/";
          }}>Trang chủ</Button
        >
        <Button
          color="danger"
          on:click={() => {
            push("/invoice");
          }}>Đơn mua</Button
        >
      </ModalFooter>
    </Modal>
  </Container>
  <Footer />
</Container>
