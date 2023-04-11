<template>
  <div class="card">
    <div class="card-header pb-0">
      <h5 class="card-title mb-0">Видеокарта</h5>
    </div>
    <div class="card-body">
      <apexchart
          type="pie"
          height="190"
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
      chart: {
        width: '100%',
        type: 'pie',
      },
      labels: ["AMD", "Intel"],
    }

    const series = ref([])

    fetch('https://localhost:7032/VideoCarts')
        .then(response => response.json())
        .then(data => series.value = data.map((item: { value: number }) => item.value))

    return { options, series }
  }
})
</script>

<style lang="scss" scoped>

</style>
