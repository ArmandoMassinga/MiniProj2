<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Adicionar Expert" />
      <!--FORM-->
      <b-row>
        <b-col cols="2"></b-col>
        <b-col cols="8">
          <form @submit.prevent="add">
            <div class="form-group">
              <input
                v-model="name"
                type="text"
                class="form-control form-control-lg"
                id="txtName"
                placeholder="escreve nome"
                required
              />
            </div>
            <div class="form-group">
              <select
                id="sltType"
                class="form-control form-control-lg"
                v-model="type"
                required
              >
                <option value>-- SELECIONA GRUPO --</option>
                <option value="admin">XXXXXX</option>
                <option value="user">YYYYYYYY</option>
              </select>
            </div>
            <div class="form-group">
              <input
                v-model="birth_date"
                type="text"
                @mouseenter="this.type = 'date'"
                @mouseleave="this.type = 'text'"
                class="form-control form-control-lg"
                id="txtBirthDate"
                placeholder="escreve data de nascimento"
                required
              />
            </div>
            <div class="form-group">
              <input
                v-model="location.city"
                type="text"
                class="form-control form-control-lg"
                id="txtCity"
                placeholder="escreve cidade"
              />
            </div>
            <div class="form-group">
              <input
                v-model="location.country"
                type="text"
                class="form-control form-control-lg"
                id="txtCountry"
                placeholder="escreve país"
              />
            </div>

            <button type="submit" class="btn btn-outline-success btn-lg mr-2">
              <i class="fas fa-plus-square"></i> ADICIONAR
            </button>
            <router-link
              :to="{ name: 'listExperts' }"
              tag="button"
              class="btn btn-outline-danger btn-lg"
            >
              <i class="fas fa-window-close"></i> CANCELAR
            </router-link>
          </form>
        </b-col>
        <b-col cols="2"></b-col>
      </b-row>
    </b-container>
  </section>
</template>

<script>
import { ADD_EXPERT } from "@/store/experts/expert.constants"; // Corrigido: mantido se necessário
import HeaderPage from "@/components/HeaderPage.vue";
import router from "@/router";
import { mapGetters } from "vuex";

export default {
  name: "AddUser",
  components: {
    HeaderPage,
  },
  data: () => {
    return {
      location: { city: "", district: "", country: "" },
      auth: { username: "", password: "" },
      gamification: { points: "", quiz: "" },
      active: true,
      name: "",
      type: "",
      birth_date: "",
      description: "",
    };
  },
  computed: {
    ...mapGetters("user", ["getMessage"]),
  },
  methods: {
    add() {
      // Verifique se as senhas coincidem
      if (
        document.querySelector("#txtPassword").value !==
        document.querySelector("#txtConfirmPassword").value
      ) {
        this.$alert(
          "Campos password não coincidem",
          "Erro de validação do formulário",
          "error"
        );
      } else {
        // Usando ADD_EXPERT (se necessário) ou ADD_USER (caso esse seja o correto)
        this.$store.dispatch(`user/${ADD_EXPERT}`, this.$data).then(  // Substituir por ADD_USER caso necessário
          () => {
            this.$alert(this.getMessage, "Utilizador adicionado!", "success");
            router.push({ name: "listUsers" });
          },
          (err) => {
            this.$alert(`${err.message}`, "Erro", "error");
          }
        );
      }
    },
  },
};
</script>

<style scoped>
/* Aqui você pode adicionar estilos específicos para o componente */
</style>
