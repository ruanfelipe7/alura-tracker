<template>
  <main class="columns is-gapless is-multiline main" :class="{ 'dark-mode': isDarkModeActive }">
    <div class="column is-one-quarter">
      <BarraLateral @changedTheme="changeTheme" />
    </div>
    <div class="column is-three-quarter content">
      <FormularioTarefa @saveTask="saveTask" />
      <div class="lista">
        <TarefaItem v-for="(task, index) in tasks" :key="index" :task="task" />
        <CustomBox v-if="isListEmpty">
            Você não está muito produtivo hoje :(
        </CustomBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import FormularioTarefa from "./components/FormularioTarefa.vue";
import TarefaItem from "./components/TarefaItem.vue";
import CustomBox from './components/CustomBox.vue'
import ITask from "./interfaces/ITask";

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    CustomBox,
    FormularioTarefa,
    TarefaItem,
  },
  computed: {
    isListEmpty () : boolean {
      return this.tasks.length === 0;
    }
  },
  data() {
    return {
      tasks: [] as ITask[],
      isDarkModeActive: false,
    };
  },
  methods: {
    saveTask(task: ITask): void {
      this.tasks.push(task);
    },
    changeTheme(isDarkModeActive : boolean) {
      this.isDarkModeActive = isDarkModeActive;
    }
  },
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
.main {
  --bg-primary: #FFF;
  --text-primary: #000;
}
.main.dark-mode {
  --bg-primary: #2b2d42;
  --text-primary: #ddd;
}
.content {
  background-color: var(--bg-primary)
}
</style>
