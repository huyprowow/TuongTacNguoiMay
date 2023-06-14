<script>
    import {
    Container,

    Form,
    FormGroup,
    Input,
    Row,
    Col,
    Button,
  } from "sveltestrap";
</script>
<Container class="p-3">
    <Row>
      <Col class="ps-4">
        <h3><b> Contact </b></h3>
        <div class="ps-3">
          <p><b>Địa chỉ: </b><span>số xx phường xx quận xx TP.xx </span></p>
          <p><b>Hotline mua hàng: </b><span>0395534600</span></p>
          <p><b>Hotline bảo hành: </b><span>0395534600</span></p>
          <p><b>Email: </b><span>laptopgame.vn@gmail.com</span></p>
          <p><b>Fanpage: </b><span>Facebook.com/laptopgame.vn</span></p>
        </div>
      </Col>
      <Col>
        <h3><b>Register</b></h3>
        <Form>
          <FormGroup floating label="Tài khoản">
            <Input placeholder="Tài khoản" />
          </FormGroup>
          <FormGroup floating label="Mật khẩu">
            <Input placeholder="Mật khẩu" />
          </FormGroup>
          <Button color="dark" class="w-100">Đăng kí</Button>
        </Form>
      </Col>
    </Row>
    <Row>
      <Col class="p-0">
        <h3>
          Logo
          <Button color="secondary" style="border-radius:50%;" size="lg" class="mx-1"/>
          <Button color="secondary"  style="border-radius:50%;" size="lg" class="mx-1"/>
          <Button color="secondary"  style="border-radius:50%;" size="lg" class="mx-1"/>
          <Button color="secondary"  style="border-radius:50%;" size="lg" class="mx-1"/>
        </h3>
      </Col>
    </Row>
  </Container>