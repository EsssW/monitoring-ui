<template>
  <div class="card">
    <div class="card-header pb-0">
      <div class="d-flex justify-content-between align-items-center">
        <h5 class="card-title mb-0">Fuzzy logic</h5>
      </div>
    </div>
    <div class="card-body">
      <table class="table table-striped" style="width:100%">
        <thead>
        <tr>
          <th>#</th>
          <th>Компьютер</th>
          <th>Мощность</th>
        </tr>
        </thead>
        <tbody>
        <tr
            v-for="(item, index) in items"
            :key="index"
        >
          <td>{{ index + 1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.fuzzyLogicInfo }}</td>
        </tr>
        </tbody>
      </table>
    </div>
    <!--    <div v-if="count" class="card-footer">-->
    <!--      <nav>-->
    <!--        <ul class="pagination">-->
    <!--          <li-->
    <!--              class="page-item"-->
    <!--              :class="{ 'active': item === page }"-->
    <!--              v-for="(item, index) in count"-->
    <!--              :key="index"-->
    <!--              @click="page = item"-->
    <!--          >-->
    <!--            <span class="page-link" href="#">{{ item }}</span>-->
    <!--          </li>-->
    <!--        </ul>-->
    <!--      </nav>-->
    <!--    </div>-->
  </div>
</template>

<script lang="ts">
import {computed, defineComponent, ref, watch} from "vue"

export default defineComponent({
  setup() {
    // const page = ref(1)
    // const total = ref(0)
    // const count = computed(() => Math.ceil(total.value / 10))
    const items = ref([])

    const fetchData = () => fetch(`https://localhost:7032/fuzzy-logic`)
        .then(response => response.json())
        .then(data => items.value = data)

    fetchData()

    // watch(page, fetchData)

    return { items }
  }
})
</script>

<style lang="scss" scoped>

</style>
