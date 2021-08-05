<template>
  <div class="login-box">
  <h2>Login</h2>
  <form>
    <div class="user-box">
      <input type="text" name="" required="">
      <label>Username</label>
    </div>
    <div class="user-box">
      <input type="password" name="" required="">
      <label>Password</label>
    </div>
    <h4>
      <input type="checkbox">
      Show password
    </h4>
    <h5 class="error" hidden="true">
      Tài khoản/ mật khẩu sai kìa má
    </h5>
    <a class="btn-submit" href="#">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      Submit
    </a>
  </form>
    <h5>
      <a href="#">Forget your password?</a>
    </h5>
    <h5>
      Don't have an account?
      <a href="/register">Sign up</a>
    </h5>
</div>
</template>
