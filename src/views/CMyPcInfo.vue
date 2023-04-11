<template>
  <div class="card">
    <div class="card-header pb-0">
      <h5 class="card-title mb-0">Мой компьютер</h5>
    </div>
    <div class="card-body">
      <table class="table table-sm mt-2 mb-4">
        <tbody>
        <tr>
          <th>Название компьютера</th>
          <td>Test-название</td>
        </tr>
        <tr>
          <th>IP</th>
          <td>192.168.0.1</td>
        </tr>
        <tr>
          <th>Процессор</th>
          <td>Intel core i9 12730</td>
        </tr>
        <tr>
          <th>Видеокарта</th>
          <td>Nvidia Gefore RTX 3060</td>
        </tr>
        <tr>
          <th>Память</th>
          <td>2000 Гб</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue"

export default defineComponent({})
</script>

<style lang="scss" scoped>

</style>
