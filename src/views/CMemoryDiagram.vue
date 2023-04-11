<template>
  <div class="card">
    <div class="card-header pb-0">
      <h5 class="card-title mb-0">Объём памяти</h5>
    </div>
    <div class="card-body">
      <apexchart
          type="bar"
          :options="options"
          :series="series"
      ></apexchart>
    </div>
  </div>
</template>

<script lang="ts">
import {defineComponent, ref} from "vue"
import VueApexCharts from "vue3-apexcharts";

export default defineComponent({
  components: {
    apexchart: VueApexCharts,
  },
  setup() {
    const options = {
      xaxis: {
        categories: [128, 256, 512, 1024, 2048],
      },
    }

    const series = ref([
      {
        name: 'Жесткий диск',
        data: []
      }
    ])

    fetch('https://localhost:7032/HDD')
        .then(response => response.json())
        .then(data => series.value[0].data = data.map((item: { value: number }) => item.value))

    return { options, series}
  }
})
</script>

<style lang="scss" scoped>

</style>
