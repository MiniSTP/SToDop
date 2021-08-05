<template>
  <div class="login-box">
    <h2>Sign up</h2>
    <form>
      <div class="user-box">
        <input type="text" name="" required="" />
        <label>Username</label>
      </div>
      <div class="user-box">
        <input type="password" name="" required="" />
        <label>Password</label>
      </div>
      <div class="user-box">
        <input type="password" name="" required="" />
        <label>Confirm Password</label>
      </div>
      <div class="user-box">
        <input type="text" name="" required="" />
        <label>Name</label>
      </div>
      <div class="user-box">
        <input type="email" name="" required="" />
        <label>Email</label>
      </div>
      <h5 class="error" hidden="true">Tài khoản/ mật khẩu sai kìa má</h5>
      <a class="btn-submit" href="#">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        Register
      </a>
    </form>
    <h5>
      Already signed up??
      <a href="/login">Sign in</a>
    </h5>
  </div>
</template>
