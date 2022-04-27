<template>
  <div id="q-app">
    <div class="q-pa-md">
      <q-btn color="primary" label="Persistent Menu">
        <q-menu persistent auto-close>
          <q-list style="min-width: 100px">
            <q-item clickable>
              <q-item-section @click="actions()" :type="type"
                >Cadastrar usuário</q-item-section
              >
            </q-item>
            <q-separator></q-separator>
            <q-item clickable>
              <q-item-section>Settings</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>
    </div>
  </div>
</template>

<script>
export default {
  props: ["type", "label", "confirmation"],
  methods: {
    actions() {
      if (this.confirmation) {
        if (confirm("Tem certeza que deseja Excluir?")) {
          this.$emit("buttonActivated");
        }
        return;
      }
      this.$emit("buttonActivated");
    },
  },
};
</script>
