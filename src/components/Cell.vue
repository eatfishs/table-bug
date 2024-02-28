<script setup lang="ts">
defineProps({
  icon: {
    type: String,
    default: "",
  },
});
</script>

<template>
  <span>
    {{ icon }}
  </span>
</template>

<style module scoped>
span {
  padding-right: 20px;
}
</style>
