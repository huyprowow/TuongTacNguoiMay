<script>
  import {
    Container,
    Row,
    Col,
    Button,
    Card,
    CardBody,
    Pagination,
    PaginationItem,
    PaginationLink,
    Form,
    FormGroup,
    Input,
  } from "sveltestrap";
  import Header from "../../component/Header.svelte";
  import Footer from "../../component/Footer.svelte";
  import productImport from "../../mocks/product/product.json";
  let radioGroup="1";
  //implement pagination exacly
  let product=productImport;
  let paginationProduct = product.slice(0, 10);
 
  let currentPage = 1;
  let pageSize = 10;
  let totalPage = Math.ceil(product.length / pageSize);
  function changePage(e, page) {
    e.preventDefault();
    currentPage = page;
    paginationProduct = product.slice(
      (currentPage - 1) * pageSize,
      currentPage * pageSize
    );
  }
  function previousPage(e) {
    e.preventDefault();
    if (currentPage > 1) {
      currentPage--;
      paginationProduct = product.slice(
        (currentPage - 1) * pageSize,
        currentPage * pageSize
      );
    }
  }
  function nextPage(e) {
    e.preventDefault();
    if (currentPage < totalPage) {
      currentPage++;
      paginationProduct = product.slice(
        (currentPage - 1) * pageSize,
        currentPage * pageSize
      );
    }
  }
  function firstPage(e) {
    e.preventDefault();

    currentPage = 1;
    paginationProduct = product.slice(
      (currentPage - 1) * pageSize,
      currentPage * pageSize
    );
  }
  function lastPage(e) {
    e.preventDefault();

    currentPage = totalPage;
    paginationProduct = product.slice(
      (currentPage - 1) * pageSize,
      currentPage * pageSize
    );
  }
</script>

<Container fluid class="p-0">
  <Header />
  <h2 class="p-3 text-center text-bg-dark">Danh sách sản phẩm</h2>

  <Form class="mx-2" style="border-bottom:1px solid lightgray;">
    <div>
      <label for="selectPrice" class="my-2"
        >Tìm theo: <b>Mức giá sản phẩm</b></label
      >
      <FormGroup>
        <Input
          type="select"
          placeholder="Chọn mức giá"
          name="select"
          id="selectPrice"
          class="form-control-sm"
          style="max-width: 200px;"
        >
          <option>&lt;5000</option>
          <option>&lt;500-&gt;7000</option>
          <option>&gt;7000</option>
        </Input>
      </FormGroup>
    </div>
    <div class="d-flex">
      <span class="me-2">Sắp xếp theo:</span>
      <FormGroup class="d-flex column-gap-2">
        <Input
          id="r1"
          type="radio"
          bind:group={radioGroup}
          value="1"
          label="Mới nhât"
          
        />
        <Input
          id="r2"
          type="radio"
          bind:group={radioGroup}
          value="2"
          label="Giá tăng dần"
        />
        <Input
          id="r3"
          type="radio"
          bind:group={radioGroup}
          value="3"
          label="Giá giảm dần"
        />
      </FormGroup>
    </div>
  </Form>
  <Row>
    {#each paginationProduct as item, idx}
      <Col>
        <Card
          class="m-2 border-0"
          style="box-shadow: 0px 4px 4px 0px #00000040; width:200px;"
        >
          <img class="card-img-top p-1" src={item.image} alt="" />
          <hr class="m-0" />
          <CardBody class="py-0">
            <ul class="list-unstyled list-inline my-2">
              {#each [0, 0, 0, 0] as item, index}
                <li class="list-inline-item mx-1">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="16"
                    height="16"
                    fill="orange"
                    class="bi bi-star-fill"
                    viewBox="0 0 16 16"
                  >
                    <path
                      d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"
                    />
                  </svg>
                </li>
              {/each}
              <li class="list-inline-item mx-0">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  fill="orange"
                  class="bi bi-star-half"
                  viewBox="0 0 16 16"
                >
                  <path
                    d="M5.354 5.119 7.538.792A.516.516 0 0 1 8 .5c.183 0 .366.097.465.292l2.184 4.327 4.898.696A.537.537 0 0 1 16 6.32a.548.548 0 0 1-.17.445l-3.523 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256a.52.52 0 0 1-.146.05c-.342.06-.668-.254-.6-.642l.83-4.73L.173 6.765a.55.55 0 0 1-.172-.403.58.58 0 0 1 .085-.302.513.513 0 0 1 .37-.245l4.898-.696zM8 12.027a.5.5 0 0 1 .232.056l3.686 1.894-.694-3.957a.565.565 0 0 1 .162-.505l2.907-2.77-4.052-.576a.525.525 0 0 1-.393-.288L8.001 2.223 8 2.226v9.8z"
                  />
                </svg>
              </li>
            </ul>
            <p>
              <b>Tên: </b>
              <span>{item.name}</span>
            </p>
            <p>
              <b>Thông số: </b>
              <span>{item.desc}</span>
            </p>
            <p>
              <b>Giá: </b>
              <span>{item.price}</span>
            </p>
          </CardBody>
        </Card>
      </Col>
    {/each}
  </Row>
  <Pagination
    aria-label="Page navigation example"
    class="d-flex justify-content-center m-2"
  >
    <PaginationItem>
      <PaginationLink first on:click={(e) => firstPage(e)} class="text-dark" />
    </PaginationItem>
    <PaginationItem>
      <PaginationLink
        previous
        on:click={(e) => previousPage(e)}
        class="text-dark"
      />
    </PaginationItem>
    {#each [1, 2] as item, index}
      <PaginationItem>
        <PaginationLink
          on:click={(e) => changePage(e, index + 1)}
          class={currentPage == index + 1
            ? "bg-danger text-white"
            : "text-dark"}
        >
          {index + 1}
        </PaginationLink>
      </PaginationItem>
    {/each}
    <PaginationItem>
      <PaginationLink next on:click={(e) => nextPage(e)} class="text-dark" />
    </PaginationItem>
    <PaginationItem>
      <PaginationLink last on:click={(e) => lastPage(e)} class="text-dark" />
    </PaginationItem>
  </Pagination>
  <Footer />
</Container>
