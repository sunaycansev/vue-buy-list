<template>
  <div class="mb-3">
    <input type="text" placeholder="Ne alınacak ?" @keydown.enter="onSave" />
  </div>
</template>

<script>
export default {
  name: "AddSection",
  props: {
    onSave: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style scoped></style>
