<template>
  <div class="loginContent">
    <q-img
      src="https://convicti.com.br/assets/images/r_footer-logo.webp"
      alt="Convicti logomarca"
      class="imageLogin"
    />
    <q-form class="loginForm" @submit="onSubmit" id="form">
      <div>
        <label for="email">E-mail</label>
        <q-input
          v-model="form.email"
          input-class="inputClassForm"
          bg-color="white"
          color="secondary"
          type="email"
          :rules="inputValidation"
          outlined
        />
      </div>
      <div class="q-my-sm">
        <label for="email">Senha</label>
        <q-input
          v-model="form.password"
          input-class="inputClassForm"
          bg-color="white"
          color="secondary"
          type="password"
          :rules="inputValidation"
          outlined
        />
      </div>
      <q-btn
        padding="10px 0"
        class="buttonForm"
        type="submit"
        color="accent"
        label="Entrar"
      />
    </q-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      error: false,
      loading: false,
      form: {
        email: null,
        password: null,
      },
      inputValidation: [
        (val) => (val && val.length > 0) || 'Campo obrigatório',
      ],
    };
  },
  methods: {
    onSubmit() {
      window.localStorage.setItem('token', 'nd93ND948N84GFBVDFVB72');
      this.$router.push('/');

      // try {
      //     this.loading = true
      //   await login({ ...this.form }).then((res) => {
      //     this.login = false;

      //     if (!res.access_token) {
      //       this.error = true
      //       return;
      //     }
      //   });
      // } catch (error) {
      //   console.log(error)
      // } finally{
      //   this.loading = false
      // }
    },
  },
};
</script>

<style lang="sass">
.loginContent
  display: flex
  align-items: center
  justify-content: center
  flex-direction: column
  background-color: $bgPrimary
  height: 100vh
  color: $labelsSecondary

.imageLogin
  max-width: 400px
  top: -100px

.loginForm
  width: 30%
  font-size: 16px

.inputClassForm
  font-size: 16px

.q-field__control
  height:44px

.buttonForm
  width: 100%
  margin-top: 12px
</style>
