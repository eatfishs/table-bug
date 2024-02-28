<template>
  <div>
    <Button
      v-for="(item, idx) in basicColumns"
      :key="idx"
      @click="item.show = !item.show"
      >{{ item.title }}</Button
    >
  </div>
  <Table :dataSource="dataSource" :columns="columns">
    <template #bodyCell="data">
      <template v-if="data.column.dataIndex === 'name'">name </template>
      <template v-if="data.column.dataIndex === 'age'"
        ><Cell icon="eye-filled" />
        <Cell
          icon="download"
          :class="!data.record.originalInfo ? 'cursor-disabled' : ''"
        />
      </template>
      <template v-if="data.column.dataIndex === 'address'"
        ><Cell icon="eye-filled" />
        <Cell icon="delete-filled" />
      </template>
    </template>
  </Table>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import { Table, Button } from "ant-design-vue";
import Cell from "./Cell.vue";
// 将这里注释掉后就不会出现问题
// :class="!data.record.originalInfo ? 'cursor-disabled' : ''"
const basicColumns = ref([
  {
    title: "姓名",
    dataIndex: "name",
    key: "name",
    show: true,
  },
  {
    title: "年龄",
    dataIndex: "age",
    key: "age",
    show: true,
  },
  {
    title: "住址",
    dataIndex: "address",
    key: "address",
    show: true,
  },
]);

const columns = computed(() => {
  return basicColumns.value.filter((item) => item.show);
});

const dataSource = [{}];
</script>

<style scoped lang="less"></style>
