<template>
  <div
    class="veenaa-pop"
    :style="{ top: veenaaPopItem.y + 'px', left: veenaaPopItem.x + 'px' }"
  ></div>
</template>

<script lang="ts">
import Vue, { PropOptions } from 'vue'
import { Veenaa } from '~/pages/veenaa-pop.vue'

export default Vue.extend({
  props: {
    veenaaPopItem: {
      type: Object,
      required: true,
    } as PropOptions<Veenaa>,
  },
  mounted() {
    setTimeout(() => this.$emit('expired', this.veenaaPopItem.id), 2400)
  },
})
</script>

<style lang="scss">
.veenaa-pop {
  position: absolute;
  background: url('~assets/veenaa.PNG');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  pointer-events: none;
  transform: translate(-50%, -50%);
  animation: animate 2.5s linear 1;
  width: 77.4427px;
  height: 77.4427px;
  opacity: 1;
}

@keyframes animate {
  0% {
    transform: translate(-50%, -50%);
    opacity: 1;
  }

  100% {
    transform: translate(-50%, -300%);
    opacity: 0;
  }
}
</style>
