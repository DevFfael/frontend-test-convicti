<template>
  <q-layout view="lHh lpR lFf">
    <side-bar />
    <q-page-container class="mainContainer">
      <header-main />
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import SideBar from 'src/components/SideBar.vue';
import HeaderMain from 'src/components/HeaderMain.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'MainLayout',
  components: { SideBar, HeaderMain },
});
</script>

<style lang="sass">
.mainContainer
  padding-left: 360px !important
  background-color: $bgSecondary
  height: 100vh
</style>
