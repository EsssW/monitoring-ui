<template>
  <div class="card">
    <div class="card-header pb-0">
      <h5 class="card-title mb-0">Объём оперативной памяти</h5>
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
    const options = ref({
      chart: {
        id: "vuechart-example",
      },
      xaxis: {
        categories: ["2", "3", "4", "6", "8", "12", "16", "32", "64", "128"],
      },
    })

    const series = ref([
      {
        data: [],
      },
    ])

    fetch('https://localhost:7032/RAM')
        .then(response => response.json())
        .then(data => {
          options.value.xaxis.categories = data.map((item: { name: string }) => item.name)
          series.value[0].data = data.map((item: { value: number }) => item.value)
        })

    return { options, series }
  }
})
</script>

<style lang="scss" scoped>

</style>
