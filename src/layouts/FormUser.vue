<template>
  <div class="flex flex-center">
    <div class="q-gutter-md" style="max-width: 300px">
      <q-input outlined v-for="text in form" :key="text" label="text.name" />
    </div>
  </div>
</template>

<script>
export default {
  name: "FormUser",
  data() {
    return {
      form: {
        name: "",
        documentType: "",
        document: "",
        gender: "",
        phone: "",
        genderIdentity: "",
      },
    };
  },
};
</script>
