<template>
  <div style="padding: 30px; max-width: 1000px; margin: 0 auto">

    <div class="row">
      <div class="col-md-6">
        <c-my-pc-info />
      </div>
      <div class="col-md-6">
        <c-processor-diagram />
      </div>
      <div class="col-md-6">
        <c-ram-diagram />
      </div>
      <div class="col-md-6">
        <c-memory-diagram />
      </div>
    </div>

    <c-pc-info-table />

    <c-fuzzy-logic />

    <c-accossiation-rule />

  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue"
import CPcInfoTable from "@/views/CPcInfoTable.vue";
import CRamDiagram from "@/views/CRamDiagram.vue";
import CProcessorDiagram from "@/views/CProcessorDiagram.vue";
import CMyPcInfo from "@/views/CMyPcInfo.vue";
import CMemoryDiagram from "@/views/CMemoryDiagram.vue";
import CAccossiationRule from "@/views/CAccossiationRule.vue";
import CFuzzyLogic from "@/views/CFuzzyLogic.vue";

export default defineComponent({
  components: {CFuzzyLogic, CAccossiationRule, CMemoryDiagram, CMyPcInfo, CProcessorDiagram, CRamDiagram, CPcInfoTable}
})
</script>

<style lang="scss" scoped>

</style>
