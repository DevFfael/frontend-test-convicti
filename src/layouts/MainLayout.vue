<template>
  <q-layout view="lHh lpR lFf">
    <side-bar />
    <q-page-container class="mainContainer">
      <q-page>
        <header-main @modal="handleModal" />
        <map-main />
        <router-view />
      </q-page>
      <add-companies @close="handleModal" :open="openModal" />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import SideBar from 'src/components/SideBar.vue';
import HeaderMain from 'src/components/HeaderMain.vue';
import MapMain from 'src/components/MapMain.vue';
import AddCompanies from 'src/components/AddCompanies.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'MainLayout',
  components: { SideBar, HeaderMain, MapMain, AddCompanies },
  data() {
    return {
      openModal: false,
    };
  },
  mounted() {
    const token = localStorage.getItem('token');
    if (!token) {
      this.$router.push('/login');
    }
  },
  methods: {
    handleModal(value: any) {
      this.openModal = value;
    },
  },
});
</script>

<style lang="sass">
.mainContainer
  padding-left: 360px !important
  background-color: $bgSecondary
  height: 100vh
</style>
