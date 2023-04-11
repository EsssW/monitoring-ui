<template>
  <div class="card">
    <div class="card-header pb-0">
      <div class="d-flex justify-content-between align-items-center">
        <h5 class="card-title mb-0">Список компьютеров</h5>
      </div>
    </div>
    <div class="card-body">
      <table class="table table-striped" style="width:100%">
        <thead>
        <tr>
          <th>#</th>
          <th>IP</th>
          <th>Процессор</th>
          <th>Видеокарта</th>
          <th>Память</th>
        </tr>
        </thead>
        <tbody>
        <tr
          v-for="(item, index) in items"
          :key="index"
        >
          <td>{{ (page - 1) * 10 + index + 1 }}</td>
          <td>{{ item.pcipV4 }}</td>
          <td>{{ item.cpuModel }}</td>
          <td>{{ item.videoCardName }}</td>
          <td>{{ item.hddSize }}</td>
        </tr>
        </tbody>
      </table>
    </div>
    <div v-if="count" class="card-footer">
      <nav>
        <ul class="pagination">
          <li
              class="page-item"
              :class="{ 'active': item === page }"
              v-for="(item, index) in count"
              :key="index"
              @click="page = item"
          >
              <span class="page-link" href="#">{{ item }}</span>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script lang="ts">
import {computed, defineComponent, ref, watch} from "vue"

export default defineComponent({
  setup() {
    const page = ref(1)
    const total = ref(0)
    const count = computed(() => Math.ceil(total.value / 10))
    const items = ref([])

    const fetchData = () => fetch(`https://localhost:7032/Paginate?page=${page.value}`)
        .then(response => response.json())
        .then(data => {
          items.value = data.items
          total.value = data.total
        })

    fetchData()

    watch(page, fetchData)

    return { page, count, items }
  }
})
</script>

<style lang="scss" scoped>

</style>
