<script>
  import {
    Container,
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
  import Header from "../../component/Header.svelte";
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
  let bgStyle = [
    'border:1px solid  rgba(255, 236, 210, 0.6); border-radius: 10px; box-shadow: 0px 4px 4px 0px #00000040; background-color:  rgba(255, 236, 210, 0.6);"',
    "border:1px solid white; border-bottom-left-radius: 10px; border-bottom-right-radius: 10px; box-shadow: 0px 4px 4px 0px #00000040;",
  ];
  const topProduct = product.slice(0, 5);
</script>

<Container fluid class="p-0">
  <Header />
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
    <ListCard {topProduct} title={type[0]} bgStyle={bgStyle[0]} />
    <ListCard {topProduct} title={type[1]} bgStyle={bgStyle[1]} />
    <ListCard {topProduct} title={type[2]} bgStyle={bgStyle[0]} />
  </Container>
  <Footer />
</Container>
