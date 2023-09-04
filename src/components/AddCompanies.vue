<template>
  <section ref="wrapper" id="addCompanies" :class="`${open ? 'show' : 'hide'}`">
    <div class="register">
      <h4>Cadastrar empresa</h4>
      <q-form @submit="onSubmit" @reset="onReset">
        <div class="form">
          <div class="left">
            <div class="input">
              <label for="c-name">Nome</label>
              <input
                type="text"
                v-model="company.name"
                id="c-name"
                name="c-name"
                required
              />
            </div>

            <div class="input">
              <label for="c-cnpj">CNPJ</label>
              <input
                type="text"
                v-model="company.cnpj"
                id="c-cnpj"
                name="c-cnpj"
                required
              />
            </div>

            <div class="input">
              <label for="c-email">E-mail</label>
              <input
                type="email"
                v-model="company.email"
                id="c-email"
                name="c-email"
                required
              />
            </div>

            <div class="input">
              <label for="c-whatsapp">Whatsapp</label>
              <input
                type="text"
                v-model="company.whatsapp_phone"
                id="c-whatsapp"
                name="c-whatsapp"
                required
              />
            </div>

            <div class="input">
              <label for="c-rep">Representante</label>
              <input
                type="text"
                v-model="company.representantive_user"
                id="c-rep"
                name="c-rep"
              />
            </div>

            <div class="twice">
              <div class="input">
                <label for="c-lat">Latitude</label>
                <input
                  type="text"
                  v-model="company.latitude"
                  id="c-lat"
                  name="c-lat"
                  class="short"
                  required
                />
              </div>
              <div class="input">
                <label for="c-log">Longitude</label>
                <input
                  type="text"
                  v-model="company.longitude"
                  id="c-log"
                  name="c-log"
                  class="short"
                  required
                />
              </div>
            </div>
            <div class="twice">
              <div class="input">
                <label for="c-estado">Estado</label>
                <select
                  v-model="company.state_id"
                  class="input-select"
                  name="c-estado"
                  id="c-estado"
                >
                  <option value="">Selecione</option>
                  <option
                    v-for="$state in states"
                    :key="$state.id"
                    :value="$state.id"
                  >
                    {{ $state.letter }}
                  </option>
                </select>
              </div>
              <div class="input">
                <label for="c-rep">Cidade</label>
                <input
                  type="text"
                  v-model="company.city"
                  id="c-rep"
                  name="c-rep"
                />
              </div>
            </div>
          </div>
          <div class="right">
            <div class="input">
              <label for="c-observations">Observações</label>
              <input
                type="text"
                v-model="company.notes"
                id="c-observations"
                name="c-observations"
              />
            </div>
            <div class="input">
              <label for="c-category">Categoria</label>
              <select
                class="input-select"
                name="c-category"
                id="c-category"
                required
                v-model="company.category_id"
              >
                <option value="">Selecione</option>
                <option
                  v-for="$category in categories"
                  :key="$category.id"
                  :value="$category.id"
                >
                  {{ $category.name }}
                </option>
              </select>
            </div>
          </div>
        </div>
        <div class="buttons">
          <button type="reset" class="cancel">Cancelar</button>
          <button type="submit" class="submit">cadastrar empresa</button>
        </div>
      </q-form>
    </div>
  </section>
</template>

<script>
import { defineComponent, ref } from 'vue';
// mocks
import {
  categories as $categories,
  states as $states,
} from 'src/composables/mock.companies';

// const { getCategories, getStates, getCitiesByState, addCompany } = useApi();

export default defineComponent({
  name: 'AddCompanies',
  emits: ['close'],
  props: {
    open: {
      type: Boolean,
      default: false,
    },
  },
  setup() {
    const categories = ref($categories);
    const states = ref($states);

    const company = ref({
      name: '',
      email: '',
      cnpj: '',
      whatsapp_phone: '',
      representantive_user: '',
      category_id: '',
      city: '',
      state_id: '',
      latitude: '',
      longitude: '',
      notes: '',
    });

    return { categories, states, company };
  },
  methods: {
    onReset() {
      this.company = {
        name: '',
        email: '',
        cnpj: '',
        whatsapp_phone: '',
        representantive_user: '',
        category_id: '',
        city: '',
        state_id: '',
        latitude: '',
        longitude: '',
        notes: '',
      };
      this.$emit('close', false);
    },
    async onSubmit() {
      console.log('Cadastrando...');
      this.$emit('close', false);
    },
  },
});
</script>

<style lang="scss" scoped>
#addCompanies {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100%;
  display: grid;
  place-items: flex-end;
  z-index: 50;
  transition: all 0.3s cubic-bezier(0.165, 0.84, 0.44, 1);

  &.show {
    transform: translateX(0);
    opacity: 1;
    pointer-events: all;

    animation: bg 0.3s ease-in forwards;
    animation-delay: 0.2s;

    @keyframes bg {
      0% {
        background-color: rgba(0, 0, 0, 0);
      }
      100% {
        background-color: rgba(0, 0, 0, 0.3);
      }
    }
  }

  &.hide {
    pointer-events: none;
    transform: translateX(50%);
    opacity: 0;
  }

  .register {
    @media screen and (max-width: 425px) {
      width: 100%;
    }

    background: red;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    padding: 2rem 6rem;

    h4 {
      font-size: 2.2rem;
      font-weight: 700;
      text-transform: capitalize;
      color: $labels;
      margin-bottom: 1rem;

      @media screen and (max-width: 375px) {
        width: 25rem !important;
      }
    }

    @media screen and (min-width: 1440px) {
      width: 55vw;
      overflow-y: auto;
      padding: 2rem 10rem;
    }

    width: 100%;
    overflow-y: auto;
    height: 100vh;
    background: $bgSecondary;

    .form {
      display: flex;
      justify-content: start;
      column-gap: 4rem;

      @media screen and (max-width: 1370px) {
        width: 55%;
      }

      @media screen and (max-width: 425px) {
        flex-direction: column;
        align-items: center;
        width: 100%;
      }
    }
  }

  .input {
    margin: 1rem 0;
    display: flex;
    flex-direction: column;

    label {
      font-size: 1rem;
      font-weight: 600;
      color: $labels;
      margin-bottom: 0.5rem;
    }

    input {
      text-indent: 0.6rem;
      font-size: 1rem;
      font-weight: 600;
      color: $labels;
      background-color: white;
      outline: none;
      border: none;
      height: 3.5rem;
      border-radius: 0.4rem;
      box-shadow: 0 0 0.3rem rgba(0, 0, 0, 0.1);
      width: 25rem;

      &::placeholder {
        color: $labels;
      }
    }
  }

  .twice {
    display: flex;
    width: 25rem;
    column-gap: 1rem;

    input,
    select {
      width: calc(15rem - 0.5rem);
    }
  }

  select {
    font-size: 1rem;
    text-indent: 0.5rem;
    font-weight: 600;
    color: $labels;
    background-color: white;
    outline: none;
    border: none;
    height: 3.5rem;
    border-radius: 0.4rem;
    box-shadow: 0 0 0.3rem rgba(0, 0, 0, 0.1);
    width: 25rem;
    background-size: 2rem;
    padding-right: 0.4rem;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    background-image: url('/icons/angle-small-down.svg');
    background-repeat: no-repeat;
    background-position-x: 98%;
    background-position-y: 50%;
    background-color: white;
    background-size: 2rem;
    padding-right: 0.4rem;

    option {
      font-size: 1rem;
      font-weight: 600;
      color: $labels;
      background-color: $bgSecondary;
      outline: none;
      border: none;
      height: 3.5rem;
      border-radius: 0.4rem;
      box-shadow: 0 0 0.3rem rgba(0, 0, 0, 0.1);
      width: 25rem;
    }
  }

  .buttons {
    margin-top: 4rem;
    display: flex;
    justify-content: center;
    column-gap: 0.8rem;

    @media screen and (max-width: 425px) {
      flex-direction: column;
      align-items: center;
      row-gap: 0.8rem;
      width: 100%;
    }

    button {
      border: none;
      outline: none;
      text-align: center;
      text-transform: capitalize;
      font-size: 1rem;
      font-weight: 600;
      width: 24rem;
      padding: 1.8rem 0;
      border-radius: 0.8rem;
      cursor: pointer;

      &:active {
        transform: scale(0.98);
      }

      &.cancel {
        background-color: #e0e0e0;
        color: $labels;
        box-shadow: 0 0 0.3rem rgba(0, 0, 0, 0.1);
      }

      &.submit {
        background-color: $labels;
        color: $bgSecondary;
        box-shadow: 0 0 0.3rem rgba(0, 0, 0, 0.1);
      }
    }
  }
}
</style>
