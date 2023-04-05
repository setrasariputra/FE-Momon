<template>
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
          v-model="form.email"
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
        <input
          v-model="form.password"
          type="password"
          name="password"
          placeholder="******"
          class="forminput"
          required
        />
      </div>
    </div>
    <a href="#" class="button-secondary">Lupa Password</a>
    <input type="submit" value="Login" @click.prevent="onSubmit" class="button-primary" />
  </form>
  <!-- End Block Form -->
</template>

<script>
import axios from "axios";
export default {
  name: 'LoginForm',
  data() {
    return {
      title: 'Selamat Data',
      urlLogin: 'http://localhost:8000/api/v1/login',
      form: {
        email: '',
        password: '',
      },
      active: true
    }
  },
  created() {
    console.log("Created");
  },
  methods: {
    async onSubmit() {
      try {
        // sukses
        const response = await axios({
          method: "post",
          url: this.urlLogin,
          data: this.form,
        });
        if(response.data.status == 'success') {
          const access_token = response.data.access_token;
          const expired_token = response.data.expires_in;

          // save to localStorage
          localStorage.setItem("access_token",access_token);
          localStorage.setItem("expired_token",expired_token);

          // redirect dashboard
          console.log("Sukses Login "+access_token);
        }
      } catch (error) {
        // error
        console.log(error);
      }
    }
  }
}
</script>

<style scoped></style>
