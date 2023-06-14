<script>
  import {
    Container,
    Navbar,
    NavbarBrand,
    NavItem,
    NavLink,
    Nav,
    Form,
    FormGroup,
    Label,
    Input,
    Carousel,
    CarouselControl,
    CarouselIndicators,
    CarouselItem,
    Row,
    Col,
    Button,
  } from "sveltestrap";
  import "./Home.scss";
  import img1 from "../../assets/image/maytinh1.jpg";
  import img2 from "../../assets/image/maytinh2.jpg";
  import img3 from "../../assets/image/maytinh3.jpg";
  import Footer from "../../component/Footer.svelte";
  import ListCard from "../../component/ListCard.svelte";
  const items = [img1, img2, img3];
  import product from "../../mocks/product/product.json";
  let activeIndex = 0;
  setInterval(() => {
    activeIndex = activeIndex === items.length - 1 ? 0 : activeIndex + 1;
  }, 3000);
  const brand = [
    "Macbook",
    "Dell",
    "Asus",
    "HP",
    "Lenovo",
    "Acer",
    "MSI",
    "Khác",
  ];
  let type = ["Laptop giá rẻ", "Chơi game - Lập trình", "Hàng giảm giá"];
  let bgStyle=[
    'border:1px solid  rgba(255, 236, 210, 0.6); border-radius: 10px; box-shadow: 0px 4px 4px 0px #00000040; background-color:  rgba(255, 236, 210, 0.6);"',
    'border:1px solid white; border-bottom-left-radius: 10px; border-bottom-right-radius: 10px; box-shadow: 0px 4px 4px 0px #00000040;'
  ]
</script>

<Container fluid class="p-0">
  <Navbar id="home_nav" expand="md" class="ps-5" light color="light">
    <NavbarBrand href="/">Logo</NavbarBrand>
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
      <NavItem>
        <NavLink href="/login" style="color:black;">Đăng nhập/Đăng kí</NavLink>
      </NavItem>
    </Nav>
  </Navbar>
  <Carousel {items} bind:activeIndex>
    <CarouselIndicators bind:activeIndex {items} />

    <div class="carousel-inner">
      {#each items as item, index}
        <CarouselItem bind:activeIndex itemIndex={index}>
          <img src={item} class="d-block w-100" alt={`${item} ${index + 1}`} />
        </CarouselItem>
      {/each}
    </div>

    <CarouselControl direction="prev" bind:activeIndex {items} />
    <CarouselControl direction="next" bind:activeIndex {items} />
  </Carousel>
  <Container fluid class="p-0">
    <Row
      class="py-2 m-0"
      style="border:1px solid white; border-bottom-left-radius: 10px; border-bottom-right-radius: 10px; box-shadow: 0px 4px 4px 0px #00000040;"
    >
      <h2 class="text-center p-0">Thương hiệu laptop</h2>
      {#each brand as item, index}
        <Col class="text-center py-2">
          <svg
            width="52"
            height="50"
            viewBox="0 0 52 50"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M1 33.0398L1 2.42399C1 1.63754 1.67157 1 2.5 1L49.5 1C50.3285 1 51 1.63754 51 2.42399V33.0398M1 33.0398L1 37.5491C1 38.3357 1.67157 38.9731 2.5 38.9731L49.5 38.9731C50.3285 38.9731 51 38.3357 51 37.5491V33.0398M1 33.0398L51 33.0398M18.5 48.4664H22.25M22.25 48.4664V38.9731M22.25 48.4664H29.75M29.75 48.4664H33.5M29.75 48.4664V38.9731"
              stroke="black"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          <p>{item}</p>
        </Col>
      {/each}
    </Row>
    <ListCard {product} title={type[0]} bgStyle={bgStyle[0]}/>
    <ListCard {product} title={type[1]} bgStyle={bgStyle[1]}/>
    <ListCard {product} title={type[2]} bgStyle={bgStyle[0]}/>
  </Container>
  <Footer />
</Container>
