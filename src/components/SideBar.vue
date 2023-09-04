<template>
  <q-drawer
    v-model="drawer"
    show-if-above
    class="sidebarContent"
    :right="position === 'right'"
    :breakpoint="breakpoint"
  >
    <div class="imgSidebar">
      <q-img
        src="https://convicti.com.br/assets/images/r_footer-logo.webp"
        alt="Convicti logomarca"
        img-class="imgClassSidebar"
      />
    </div>

    <div class="container">
      <div>
        <p>MENU</p>
        <q-btn
          unelevated
          no-caps
          align="left"
          icon="domain"
          label="Empresas"
          class="btnMenu"
        />
      </div>

      <q-btn
        flat
        label="Sair"
        @click="logout"
        icon="power_settings_new"
        class="btnExit"
      />
    </div>
  </q-drawer>
</template>

<script>
export default {
  data() {
    return {
      drawer: true,
      position: 'left',
      breakpoint: 992,
    };
  },
  methods: {
    logout() {
      window.localStorage.removeItem('token');
      this.$router.push('/login');
    },
  },
};
</script>

<style lang="sass">
p
  font-size: 18px

.sidebarContent
  display: flex
  flex-direction: column
  width: 360px !important
  padding: 48px 48px
  background-color: $bgPrimary
  height: 100%
  color: $labelsSecondary

.container
  display: flex
  flex-direction: column
  justify-content: space-between
  margin-top: 120px
  height: 100%

.btnMenu
  background-color: $bgSecondary
  font-size: 16px
  color: $labels
  width: 100%
  height: 48px
  border-radius: 4px

.labelField
  font-size: 16px

.imgSidebar
  max-width: 100%
  margin-top: 40px

.imgClassSidebar
  object-fit: contain !important

.btnExit
  width: fit-content
</style>
