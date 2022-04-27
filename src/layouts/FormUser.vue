<template>
  <q-page class="container" padding>
    <p class="text-h4">Formulário</p>
    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="row q-col-gutter-md"
      ref="myForm"
    >
      <q-input
        outlined
        v-model="form.nome"
        color="deep-purple"
        label="Nome"
        class="col-md-12 col-sm-12 col-xs-12"
        :rules="[(val) => (val && val.length > 0) || 'Nome obrigatório']"
      >
        <template v-slot:prepend>
          <q-icon name="person" />
        </template>
      </q-input>

      <q-select
        outlined
        v-model="form.documentType"
        :options="optionsDocumentType"
        label="Tipo de documento"
        class="col-md-4 col-sm-4 col-xs-4"
        emit-value
        map-options
      />

      <q-input
        outlined
        v-model="form.document"
        color="deep-purple"
        label="Documento"
        class="col-md-8 col-sm-8 col-xs-8"
        :rules="[(val) => (val && val.length > 0) || 'Documento obrigatório']"
      >
      </q-input>

      <q-input
        v-model="form.email"
        label="Email"
        outlined
        class="col-md-12 col-sm-12 col-xs-12"
        :rules="[(val) => (val && val.length > 0) || 'Email obrigatório']"
      >
        <template v-slot:prepend>
          <q-icon name="mails" />
        </template>
      </q-input>

      <q-input
        v-model="form.telefone"
        label="Telefone"
        outlined
        class="col-md-8 col-sm-8 col-xs-8"
        mask="(##) #####-####"
        unmasked-value
        :rules="[
          (val) => (val && val.length > 0) || 'Telefone obrigatório',
          (val) => val.length === 11 || 'Coloque um telefone real',
        ]"
      />

      <q-select
        outlined
        v-model="form.genderIdentity"
        :options="optionsGenderIdentity"
        label="Gênero"
        class="col-md-4 col-sm-4 col-xs-4"
        emit-value
        map-options
      />

      <div class="col-12">
        <q-btn
          label="Cadastrar Endereço"
          type="submit"
          color="primary"
          class="float-right"
        />
        <q-btn
          label="Resetar"
          type="reset"
          color="default"
          class="float-right text-grey-10 q-mr-md"
        />
      </div>
    </q-form>
  </q-page>
</template>

<script>
export default {
  name: "PageIndex",
  data() {
    return {
      form: {
        nome: "",
        documentType: "",
        document: "",
        gender: "",
        email: "",
        phone: "",
        genderIdentity: "",
      },
      optionsGenderIdentity: [
        { label: "Masculino", value: "Masculino" },
        { label: "Feminino", value: "Feminino" },
        { label: "Transgênero", value: "Transgênero" },
        { label: "Intersex", value: "Intersex" },
      ],
      optionsDocumentType: [
        { label: "CPF", value: "Masculino" },
        { label: "RG", value: "Feminino" },
        { label: "CNH", value: "Transgênero" },
      ],
    };
  },
  methods: {
    onSubmit() {
      this.$q.notify({
        message: "Cadastro realizado com sucesso",
        color: "positive",
        icon: "check_circle_outline",
      });
      this.onReset();
    },
    async onReset() {
      await this.resetForm();
      this.$refs.myForm.resetValidation();
    },
    async resetForm() {
      this.form = {
        nome: "",
        documentType: "",
        document: "",
        gender: "",
        email: "",
        phone: "",
        genderIdentity: "",
      };
    },
  },
};
</script>
