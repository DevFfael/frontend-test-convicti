<template>
  <div class="row justify-between actionsHomeContent">
    <div class="col-4">
      <q-input
        v-model="search"
        outlined
        no-caps
        bg-color="white"
        color="primary"
        label="Pesquisar"
      >
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>
    </div>
    <div class="col-2">
      <q-btn
        unelevated
        no-caps
        class="btnAddCompany"
        padding="16px"
        color="secondary"
        icon-right="add"
        label="Adicionar Empresa"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: '',
    };
  },
};
</script>

<style lang="sass">
.actionsHomeContent
  padding: 20px 16px

.btnAddCompany
  color: $labels !important
  width: 100%
  border-radius: .5rem
</style>
