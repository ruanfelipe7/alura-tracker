<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTemporizador :timeSeconds="timeSeconds"/>
    <button class="button" @click="start" :disabled="isCronRunning">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="stop" :disabled="!isCronRunning">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CronometroTemporizador from "./CronometroTemporizador.vue";

export default defineComponent({
  name: "TemporizadorForm",
  components: {
    CronometroTemporizador,
  },
  data() {
    return {
      timeSeconds: 0,
      cron: 0,
      isCronRunning: false,
    };
  },
  emits: ['finishTimer'],
  methods: {
    start() {
      this.isCronRunning = true;
      this.cron = setInterval(() => {
        this.timeSeconds += 1;
      }, 1000);
    },
     
    stop() {
      this.isCronRunning = false;
      clearInterval(this.cron);
      this.$emit('finishTimer', this.timeSeconds);
      this.timeSeconds = 0;
    },
  },
});
</script>
