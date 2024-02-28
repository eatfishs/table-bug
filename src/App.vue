<template>
  <div style="width: 1000px">
    <Table>
      <template #name>name </template>
      <template #age="{ record }">
        <Cell icon="eye-filled" />
        <Cell
          icon="download"
          :class="
            !record.originalInfo ? 'cursor-disabled' : ''
          "
        />
      </template>
      <template #address>
        <Cell icon="delete-filled" />
        <Cell icon="eye-filled" />
      </template>
    </Table>
  </div>
</template>

<script setup lang="ts">
import Table from "./components/Table.vue";
import Cell from "./components/Cell.vue";
</script>

<style scoped lang="less"></style>
