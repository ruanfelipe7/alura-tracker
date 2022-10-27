<template>
  <div class="box has-text-weight-bold" :style="boxStyle">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CustomBox",
  data () {
    return {
      boxStyle: {
        backgroundColor: '#faf0ca'
      }
    }
  }
});
</script>

