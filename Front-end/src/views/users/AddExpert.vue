<template>
  <section class="page-section">
    <b-container>
      <HeaderPage title="Adicionar Expert" />

      <!-- FORM -->
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
                placeholder="Escreve nome"
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
                type="date"
                class="form-control form-control-lg"
                id="txtBirthDate"
                placeholder="Escreve data de nascimento"
                required
              />
            </div>
            <div class="form-group">
              <input
                v-model="location.city"
                type="text"
                class="form-control form-control-lg"
                id="txtCity"
                placeholder="Escreve cidade"
              />
            </div>
            <div class="form-group">
              <input
                v-model="location.country"
                type="text"
                class="form-control form-control-lg"
                id="txtCountry"
                placeholder="Escreve país"
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
