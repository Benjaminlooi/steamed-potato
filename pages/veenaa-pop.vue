<template>
  <!-- <div class="h-screen w-screen" @mousemove="spawnVeenaa($event)"> -->
  <div
    class="h-screen w-screen p-3 relative overflow-hidden full-screen-wrapper"
  >
    <div
      ref="interactiveBox"
      class="interactive-box relative overflow-hidden"
      @mousemove="spawnVeenaa($event)"
    >
      <veenaa
        v-for="veenaaPop in veenaaList"
        :key="veenaaPop.id"
        :veenaa-pop-item="veenaaPop"
        @expired="removeVeenaa(veenaaPop.id)"
      />

      <h1 class="title">Veenaa Pop</h1>

      <svg
        id="wave"
        style="transform: rotate(0deg); transition: 0.3s"
        viewBox="0 0 1440 270"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
      >
        <defs>
          <linearGradient id="sw-gradient-0" x1="0" x2="0" y1="1" y2="0">
            <stop
              stop-color="rgba(124.886, 130.944, 156.277, 1)"
              offset="0%"
            ></stop>
            <stop stop-color="rgba(41, 52, 98, 1)" offset="100%"></stop>
          </linearGradient>
        </defs>
        <path
          style="transform: translate(0, 0px); opacity: 1"
          fill="url(#sw-gradient-0)"
          d="M0,54L26.7,58.5C53.3,63,107,72,160,99C213.3,126,267,171,320,175.5C373.3,180,427,144,480,130.5C533.3,117,587,126,640,130.5C693.3,135,747,135,800,144C853.3,153,907,171,960,153C1013.3,135,1067,81,1120,85.5C1173.3,90,1227,153,1280,184.5C1333.3,216,1387,216,1440,211.5C1493.3,207,1547,198,1600,162C1653.3,126,1707,63,1760,49.5C1813.3,36,1867,72,1920,76.5C1973.3,81,2027,54,2080,54C2133.3,54,2187,81,2240,76.5C2293.3,72,2347,36,2400,27C2453.3,18,2507,36,2560,49.5C2613.3,63,2667,72,2720,99C2773.3,126,2827,171,2880,175.5C2933.3,180,2987,144,3040,144C3093.3,144,3147,180,3200,198C3253.3,216,3307,216,3360,189C3413.3,162,3467,108,3520,112.5C3573.3,117,3627,180,3680,207C3733.3,234,3787,225,3813,220.5L3840,216L3840,270L3813.3,270C3786.7,270,3733,270,3680,270C3626.7,270,3573,270,3520,270C3466.7,270,3413,270,3360,270C3306.7,270,3253,270,3200,270C3146.7,270,3093,270,3040,270C2986.7,270,2933,270,2880,270C2826.7,270,2773,270,2720,270C2666.7,270,2613,270,2560,270C2506.7,270,2453,270,2400,270C2346.7,270,2293,270,2240,270C2186.7,270,2133,270,2080,270C2026.7,270,1973,270,1920,270C1866.7,270,1813,270,1760,270C1706.7,270,1653,270,1600,270C1546.7,270,1493,270,1440,270C1386.7,270,1333,270,1280,270C1226.7,270,1173,270,1120,270C1066.7,270,1013,270,960,270C906.7,270,853,270,800,270C746.7,270,693,270,640,270C586.7,270,533,270,480,270C426.7,270,373,270,320,270C266.7,270,213,270,160,270C106.7,270,53,270,27,270L0,270Z"
        ></path>
        <defs>
          <linearGradient id="sw-gradient-1" x1="0" x2="0" y1="1" y2="0">
            <stop stop-color="rgba(236, 155, 59, 1)" offset="0%"></stop>
            <stop stop-color="rgba(242, 76, 76, 1)" offset="100%"></stop>
          </linearGradient>
        </defs>
        <path
          style="transform: translate(0, 50px); opacity: 0.9"
          fill="url(#sw-gradient-1)"
          d="M0,0L26.7,13.5C53.3,27,107,54,160,67.5C213.3,81,267,81,320,99C373.3,117,427,153,480,148.5C533.3,144,587,99,640,76.5C693.3,54,747,54,800,76.5C853.3,99,907,144,960,175.5C1013.3,207,1067,225,1120,225C1173.3,225,1227,207,1280,193.5C1333.3,180,1387,171,1440,153C1493.3,135,1547,108,1600,121.5C1653.3,135,1707,189,1760,189C1813.3,189,1867,135,1920,126C1973.3,117,2027,153,2080,166.5C2133.3,180,2187,171,2240,144C2293.3,117,2347,72,2400,58.5C2453.3,45,2507,63,2560,81C2613.3,99,2667,117,2720,121.5C2773.3,126,2827,117,2880,117C2933.3,117,2987,126,3040,148.5C3093.3,171,3147,207,3200,193.5C3253.3,180,3307,117,3360,117C3413.3,117,3467,180,3520,193.5C3573.3,207,3627,171,3680,130.5C3733.3,90,3787,45,3813,22.5L3840,0L3840,270L3813.3,270C3786.7,270,3733,270,3680,270C3626.7,270,3573,270,3520,270C3466.7,270,3413,270,3360,270C3306.7,270,3253,270,3200,270C3146.7,270,3093,270,3040,270C2986.7,270,2933,270,2880,270C2826.7,270,2773,270,2720,270C2666.7,270,2613,270,2560,270C2506.7,270,2453,270,2400,270C2346.7,270,2293,270,2240,270C2186.7,270,2133,270,2080,270C2026.7,270,1973,270,1920,270C1866.7,270,1813,270,1760,270C1706.7,270,1653,270,1600,270C1546.7,270,1493,270,1440,270C1386.7,270,1333,270,1280,270C1226.7,270,1173,270,1120,270C1066.7,270,1013,270,960,270C906.7,270,853,270,800,270C746.7,270,693,270,640,270C586.7,270,533,270,480,270C426.7,270,373,270,320,270C266.7,270,213,270,160,270C106.7,270,53,270,27,270L0,270Z"
        ></path>
      </svg>
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
  layout: 'fullscreen',
  data: () => ({
    count: 0,
    veenaaList: [] as Veenaa[],
  }),
  methods: {
    spawnVeenaa(e: MouseEvent) {
      // Get the target
      const target = this.$refs.interactiveBox as HTMLElement

      // Get the bounding rectangle of target
      const rect = target.getBoundingClientRect()

      // Mouse position
      const x = e.clientX - rect.left
      const y = e.clientY - rect.top

      this.veenaaList.push({ id: this.count++, x, y })
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
@import url('https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap');

.full-screen-wrapper {
  background-color: #d88787;
  font-family: 'Permanent Marker', cursive;

  .interactive-box {
    height: 100%;
    width: 100%;
    border-radius: 16px;
    background-color: #e5a7a7;
  }

  .title {
    text-align: center;
    font-size: 3rem;
    margin-top: 2rem;
    color: #d8878769;
  }

  #wave {
    position: absolute;
    width: 100%;
    bottom: 0;
    opacity: 0.2;
  }
}
</style>
