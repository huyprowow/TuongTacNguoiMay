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
  import invoiceImport from "../../mocks/invoice/invoice.json";

  let invoices = invoiceImport;
  let open = false;
  const toggle = (id) => {
    open = !open;
  };
  let openSuccess = false;
  const toggleSuccess = () => {
    toggle();
    openSuccess = !openSuccess;
  };

  //format price dollar uk
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
      <a class="text-black-50 text-decoration-none" href="/">Trang Chủ</a>
    </BreadcrumbItem>
    <BreadcrumbItem active>Giỏ hàng</BreadcrumbItem>
  </Breadcrumb>

  <Container class="text-center p-5" fluid>
    {#each invoices as invoice}
      <Row>
        <Col class="d-flex flex-grow-1 gap-3">
          <img src={invoice.image} alt="" srcset="" width="200" height="100" />
          <div>
            <h3>{invoice.name}</h3>
            <p>{invoice.desc}</p>
          </div>
          <div>
            <span style="font-size: x-large;">{formatPrice(invoice.price)}</span
            >
          </div>
        </Col>
        <Col style="max-width: max-content;">
          <Button color="warning" class="mx-2 px-4" on:click={toggle}
            >Đánh giá</Button
          >
          <Button
            color="light"
            class="border-1 border-black mx-2 px-4"
            on:click={function () {
              window.location.href = "/cart";
            }}>Mua lại</Button
          >
        </Col>
      </Row>
    {/each}

    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Đánh giá sản phẩm</ModalHeader>
      <ModalBody class="text-center">
        <div class="d-flex flex-grow-1 gap-3 p-2">
          <img
            src={invoices[0].image}
            alt=""
            srcset=""
            width="200"
            height="100"
          />
          <div>
            <h3>{invoices[0].name}</h3>
            <p>{invoices[0].desc}</p>
          </div>
        </div>
        <div class="rate">
          <input type="radio" id="star5" name="rate" value="5" />
          <label for="star5" title="text">5 stars</label>
          <input type="radio" id="star4" name="rate" value="4" />
          <label for="star4" title="text">4 stars</label>
          <input type="radio" id="star3" name="rate" value="3" />
          <label for="star3" title="text">3 stars</label>
          <input type="radio" id="star2" name="rate" value="2" />
          <label for="star2" title="text">2 stars</label>
          <input type="radio" id="star1" name="rate" value="1" />
          <label for="star1" title="text">1 star</label>
        </div>
        <Input
          type="textarea"
          style="resize: none;"
          rows={5}
          placeholder="Hãy đưa ra những trải nhiệm của bạn khi sử dụng sản phẩm và góp ý với chúng tôi khi chưa hài lòng để có hướng khắc phục nhé!!! "
        />
      </ModalBody>
      <ModalFooter class="d-flex justify-content-evenly">
        <Button
          color="light"
          class="border-1 border-black"
          on:click={() => {
            window.location.href = "/cart";
          }}>Mua lại</Button
        >
        <Button color="warning" on:click={toggleSuccess}>Hoàn thành</Button>
      </ModalFooter>
    </Modal>
    <Modal isOpen={openSuccess} toggle={toggleSuccess}>
      <ModalBody class="text-center">
        <b class="d-block"
          >Cảm ơn bạn đã đánh giá và đưa ra góp ý về sản phẩm!!</b
        >
        <span class="d-block">Chúc mừng bạn đã đánh giá thành công</span>
      </ModalBody>
      <ModalFooter class="d-flex justify-content-evenly">
        <Button
          color="light"
          class="border-1 border-black"
          on:click={() => {
            window.location.href = "/";
          }}>Trang chủ</Button
        >
        <Button
          color="danger"
          on:click={() => {
            window.location.href = "/invoice";
          }}>Quay lại</Button
        >
      </ModalFooter>
    </Modal>
  </Container>
  <Footer />
</Container>

<style>
  .rate {
    float: left;
    height: 46px;
    padding: 0 10px;
  }
  .rate:not(:checked) > input {
    position: absolute;
    top: -9999px;
  }
  .rate:not(:checked) > label {
    float: right;
    width: 1em;
    overflow: hidden;
    white-space: nowrap;
    cursor: pointer;
    font-size: 30px;
    color: #ccc;
  }
  .rate:not(:checked) > label:before {
    content: "★ ";
  }
  .rate > input:checked ~ label {
    color: #ffc700;
  }
  .rate:not(:checked) > label:hover,
  .rate:not(:checked) > label:hover ~ label {
    color: #deb217;
  }
  .rate > input:checked + label:hover,
  .rate > input:checked + label:hover ~ label,
  .rate > input:checked ~ label:hover,
  .rate > input:checked ~ label:hover ~ label,
  .rate > label:hover ~ input:checked ~ label {
    color: #c59b08;
  }
</style>
