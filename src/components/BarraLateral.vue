<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="" >
        </h1>
        <button class="button" @click="activeAndDesactiveDarkMode">
          {{ buttonText }}
        </button>
    </header>
</template>

<script lang='ts'>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BarraLateral',
    emits: ['changedTheme'],
    data () {
      return {
        isDarkModeActive: false
      }
    },
    computed: {
      buttonText () : string {
        return this.isDarkModeActive ? 'Desativar modo escuro' : 'Ativar modo escuro'; 
      }
    },
    methods: {
      activeAndDesactiveDarkMode () {
        this.isDarkModeActive = !this.isDarkModeActive;
        this.$emit('changedTheme', this.isDarkModeActive);
      }
    }
});
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>