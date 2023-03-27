<template>
  <h1>{{ title }}</h1>
  <h2>{{ inputemail }}</h2>
  <h3>{{  inputpwd }}</h3>
  <h4 v-if="active === false">Tidak Aktif</h4>
  <h4 v-else>Active</h4>
  <p v-if="old <= 25">Remaja</p>
  <p v-else-if="(old > 25) && (old <= 40)">Dewasa</p>
  <p v-else="old > 40">Orang Tua</p>

  <!-- Start Block Logo-->
  <img src="../assets/logo/momon.svg" class="mon-login-logo" />
  <!-- End Block Logo-->
  <!-- Start Block Form -->
  <form method="post" action="" class="mon-boxlogin">
    <div class="mon-rowinput">
      <img src="../assets/icon/@ at.svg" class="input-icon" />
      <div class="mon-colinput">
        <label>Email</label>
        <input
          v-model="inputemail"
          type="email"
          name="email"
          class="forminput"
          placeholder="Tulis email disini"
          required
        />
      </div>
    </div>
    <div class="mon-rowinput">
      <img src="../assets/icon/kunci.svg" class="input-icon" />
      <div class="mon-colinput">
        <label>Password</label>
        <input v-model="inputpwd" type="password" name="password" placeholder="******" class="forminput" required />
      </div>
    </div>
    <a href="#" class="button-secondary">Lupa Password</a>
    <input type="submit" value="Login" class="button-primary" />
  </form>
  <!-- End Block Form -->
</template>

<script>
export default {
  name: 'LoginForm',
  data() {
    return {
      title: 'Selamat Data',
      inputemail: '',
      inputpwd: '',
      active: true,
      old: 50,
    }
  }
}
</script>

<style scoped></style>
