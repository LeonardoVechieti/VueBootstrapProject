<template>
  <div id="app" class="container mt-3">
    <h3>Dados pessoais</h3>
    <hr />

    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-row>
        <b-col md="4" sm="12">
          <b-form-group label="Nome:" label-for="nome">
            <b-form-input
              id="nome"
              v-model="form.nome"
              placeholder="Ex: João Silva"
              required
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col md="5" sm="12">
          <b-form-group
            label="E-mail:"
            label-for="email"
            description="Seu e-mail deve ser único e não pode ter sido cadastrado."
          >
            <b-form-input
              id="email"
              v-model="form.email"
              type="email"
              placeholder="Ex: joaosilva@email.com"
              required
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col md="3" sm="12">
          <b-form-group label="Status">
            <b-form-radio-group id="status" v-model="form.status">
              <b-form-radio value="active">Ativo</b-form-radio>
              <b-form-radio value="inactive">Inativo</b-form-radio>
            </b-form-radio-group>
          </b-form-group>
        </b-col>
      </b-row>

      <b-row>
        <b-col md="4" sm="12">
          <b-form-group id="cpf" label="CPF:" label-for="cpf">
            <b-form-input
              id="cpf"
              v-model="form.cpf"
              placeholder="123.456.789-09"
              required
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col md="3" sm="12">
          <b-form-group id="rg" label="RG:" label-for="rg">
            <b-form-input
              id="rg"
              v-model="form.rg"
              placeholder="11.222.333-4"
              required
            ></b-form-input>
          </b-form-group>
        </b-col>
        <b-col md="5" sm="12">
          <b-form-group
            label="Data de nascimento:"
            label-for="dataDeNascimento"
          >
            <b-form-datepicker
              id="dataDeNascimento"
              v-model="form.dataDeNascimento"
              placeholder="dd/mm/yyyy"
              required
            ></b-form-datepicker>
          </b-form-group>
        </b-col>
      </b-row>

      <h3>Localização</h3>
      <hr />

      <b-row>
        <b-col md="4" sm="12">
          <b-form-group label="País:" label-for="pais">
            <b-form-select
              id="pais"
              v-model="form.pais"
              :options="paises"
            ></b-form-select>
          </b-form-group>
        </b-col>
        <b-col md="4" sm="12">
          <b-form-group id="estado" label="Estado:" label-for="estado">
            <b-form-select
              v-model="form.estado"
              :options="estados"
            ></b-form-select>
          </b-form-group>
        </b-col>
        <b-col md="4" sm="12">
          <b-form-group id="cidade" label="Estado:" label-for="cidade">
            <b-form-select
              v-model="form.cidade"
              :options="cidades"
            ></b-form-select>
          </b-form-group>
        </b-col>
      </b-row>

      <h3>Anexos</h3>
      <hr />

      <b-row>
        <b-col md="6" sm="12">
          <b-form-file
            @input="saveFile"
            v-model="form.file"
            placeholder="Selecione uma imagem ou arraste aqui"
          ></b-form-file>
        </b-col>
      </b-row>

      <div class="mt-3">
        <b-button type="reset" variant="warning" class="mr-3">Limpar</b-button>
        <b-button type="submit" variant="primary">Salvar</b-button>
      </div>
    </b-form>

    <b-card class="mt-3" header="Resultado">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      form: {
        nome: "",
        email: "",
        status: "",
        cpf: "",
        rg: "",
        dataDeNascimento: "",
        pais: null,
        estado: null,
        cidade: null,
        file: "",
      },
      paises: [
        { value: null, text: "Selecione uma opção" },
        { value: "BRA", text: "Brasil" },
        { value: "ARG", text: "Argentina" },
        { value: "COL", text: "Colômbia" },
      ],
      estados: [
        { value: null, text: "Selecione uma opção" },
        { value: "AC", text: "Acre" },
        { value: "AM", text: "Amazonas" },
        { value: "PA", text: "Pará" },
      ],
      cidades: [
        { value: null, text: "Selecione uma opção" },
        { value: "Rio Branco", text: "Rio Branco" },
        { value: "Manaus", text: "Manaus" },
        { value: "Belém", text: "Belém" },
      ],
      show: true,
      selected: null,
      status: null,
      file1: null,
    };
  },
  
};
</script>

<style>
</style>