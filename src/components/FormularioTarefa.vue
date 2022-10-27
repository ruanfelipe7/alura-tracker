<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para a criação de uma nova tarefa"
      >
        <input
          type="text"
          name=""
          id=""
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="description"
        />
      </div>

      <div class="column">
        <TemporizadorForm @finishTimer="finishTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TemporizadorForm from "./TemporizadorForm.vue";

export default defineComponent({
  name: "FormularioTarefa",
  components: {
    TemporizadorForm,
  },
  data () {
    return {
      description: ''
    }
  },
  emits: ['saveTask'],
  methods: {
    finishTask (timeSeconds : number) : void {
      this.$emit('saveTask', {
        durationInSeconds: timeSeconds,
        description: this.description,
      })
      this.description = '';
    }
  }
});
</script>

<style>
.form {
  background-color: var(--bg-primary);
}
</style>