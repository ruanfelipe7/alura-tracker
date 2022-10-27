<template>
  <CustomBox>
    <div class="columns">
      <div class="column is-7">{{ task.description || 'Tarefa sem descrição' }}</div>
      <div class="column">
        <CronometroTemporizador :timeSeconds="task.durationInSeconds"/>
      </div>
    </div>
  </CustomBox>
</template>

<script lang='ts'>
import { defineComponent, PropType } from "vue";
import CronometroTemporizador from "./CronometroTemporizador.vue";
import CustomBox from './CustomBox.vue'
import ITask from "../interfaces/ITask";

export default defineComponent({
  name: "TarefaItem",
  components: {
    CronometroTemporizador,
    CustomBox
  },
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true,
    },
  },
});
</script>

<style scoped>

</style>