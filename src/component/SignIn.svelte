<script>
  import {
    Form,
    FormGroup,
    Label,
    Input,
    Button,
    Container,
    NavLink,
  } from "sveltestrap";
  function handleSubmit(e) {
    e.preventDefault();
    if (e.target[0].value == "huy" && e.target[1].value == "huy") {
      localStorage.setItem("username", e.target[0].value);
      window.location.href = "/TuongTacNguoiMay/";
    }
  }
</script>

<Container>
  <h1 style="text-align: center;">Đăng nhập</h1>
  <Form on:submit={handleSubmit}>
    <FormGroup>
      <Label for="username">Tài khoản</Label>
      <Input type="text" id="username" placeholder="Tài khoản (huy)" />
    </FormGroup>
    <FormGroup>
      <Label for="password">Mật khẩu</Label>
      <Input
        type="password"
        name="password"
        id="password"
        placeholder="Mật khẩu (huy)"
      />
    </FormGroup>
    <Button style="float:right;" type="submit" color="primary">
      Đăng Nhập
    </Button>
  </Form>
</Container>
