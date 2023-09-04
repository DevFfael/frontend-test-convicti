<template>
  <div class="loginContent">
    <q-img
      src="https://convicti.com.br/assets/images/r_footer-logo.webp"
      alt="Convicti logomarca"
      class="imageLogin"
    />
    <q-form class="loginForm">
      <div class="">
        <label for="email">E-mail</label>
        <q-input
          v-model="email"
          input-class="inputClassForm"
          bg-color="white"
          color="secondary"
          type="email"
          outlined
        />
      </div>
      <div class="q-my-sm">
        <label for="email">Senha</label>
        <q-input
          v-model="password"
          input-class="inputClassForm"
          bg-color="white"
          color="secondary"
          type="password"
          outlined
        />
      </div>
      <q-btn
        padding="10px 0"
        class="buttonForm"
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
      email: null,
      password: null,
    };
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
