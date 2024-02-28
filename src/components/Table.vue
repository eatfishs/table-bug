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
      <slot :name="data.column.key" v-bind="data || {}"></slot>
    </template>
  </Table>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import { Table, Button } from "ant-design-vue";
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
