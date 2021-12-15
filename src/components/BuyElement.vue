<template>
  <li class="d-flex justify-content-between align-items-center">
    <span>{{ item.title }}</span>
    <button class="sm red" @click="onDelete(item)">Sil</button>
  </li>
</template>

<script>
export default {
  name: "BuyElement",
  props: {
    item: {
      type: Object,
      required: true,
    },
    onDelete: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style scoped></style>
