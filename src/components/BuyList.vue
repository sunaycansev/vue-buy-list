<template>
  <ul v-if="itemList.length > 0">
    <BuyElement
      v-for="item in itemList"
      :key="item.id"
      :item="item"
      :onDelete="onDelete"
    />
  </ul>
</template>

<script>
import BuyElement from "@/components/BuyElement";
export default {
  name: "BuyList",
  components: { BuyElement },
  props: {
    itemList: {
      type: Array,
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
