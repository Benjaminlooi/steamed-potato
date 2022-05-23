<template>
  <!-- <div class="h-screen w-screen" @mousemove="spawnVeenaa($event)"> -->
  <div class="h-screen w-screen p-3 full-screen-wrapper">
    <div class="interactive-box" @mousemove="spawnVeenaa($event)">
      <veenaa
        v-for="veenaaPop in veenaaList"
        :key="veenaaPop.id"
        :veenaa-pop-item="veenaaPop"
        @expired="removeVeenaa(veenaaPop.id)"
      />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import veenaa from '../components/veena-pop/veenaa.vue'

export declare interface Veenaa {
  id: number
  x: number
  y: number
}

export default Vue.extend({
  components: { veenaa },
  data: () => ({
    count: 0,
    veenaaList: [] as Veenaa[],
  }),
  methods: {
    spawnVeenaa(e: MouseEvent) {
      this.veenaaList.push({ id: this.count++, x: e.x, y: e.y })
    },
    removeVeenaa(veenaaPopID: number) {
      this.veenaaList.splice(
        this.veenaaList.findIndex((veenaa) => veenaa.id === veenaaPopID),
        1
      )
    },
  },
})
</script>

<style lang="scss">
.full-screen-wrapper {
  background-color: #d88787;
}

.interactive-box {
  height: 100%;
  width: 100%;
  border-radius: 16px;
  background-color: #e5a7a7;
}
</style>
