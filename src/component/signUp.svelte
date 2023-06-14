<script>
  import {
    Form,
    FormGroup,
    Label,
    Input,
    Button,
    Container,
  } from "sveltestrap";
</script>

<Container>
  <h1 style="text-align: center;">Đăng kí</h1>
  <Form>
    <FormGroup>
      <Label for="username">Tài khoản</Label>
      <Input type="text" id="username" placeholder="Tài khoản" />
    </FormGroup>
    <FormGroup>
      <Label for="mail">Email</Label>
      <Input type="email" id="mail" placeholder="Email" />
    </FormGroup>
    <FormGroup>
      <Label for="password">Mật khẩu</Label>
      <Input
        type="password"
        name="password"
        id="password"
        placeholder="Mật khẩu"
      />
    </FormGroup><FormGroup>
      <Label for="confirmPassword">Xác nhận lại mật khẩu</Label>
      <Input
        type="password"
        name="password"
        id="confirmPassword"
        placeholder="Xác nhận"
      />
    </FormGroup>
    <Button style="float:right;" color="primary">Đăng kí</Button>
  </Form>
</Container>
