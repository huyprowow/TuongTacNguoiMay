<script>
  import { prevent_default } from "svelte/internal";
  import {
    Form,
    FormGroup,
    Label,
    Input,
    Button,
    Container,
    NavLink,
  } from "sveltestrap";
  function handleSubmit(e){
    e.preventDefault();
    window.location.href = "/";
  }
</script>

<Container>
  <h1 style="text-align: center;">Đăng nhập</h1>
  <Form on:submit={handleSubmit}>
    <FormGroup>
      <Label for="username">Tài khoản</Label>
      <Input type="text" id="username" placeholder="Tài khoản" />
    </FormGroup>
    <FormGroup>
      <Label for="password">Mật khẩu</Label>
      <Input
        type="password"
        name="password"
        id="password"
        placeholder="Mật khẩu"
      />
    </FormGroup>
      <Button style="float:right;" type="submit" color="primary">
        Đăng Nhập
    </Button>
  </Form>
</Container>
