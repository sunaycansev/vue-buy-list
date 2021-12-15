<template>
  <div id="app">
    <div class="container">
      <AddSection :onSave="onSave" />
      <BuyList :item-list="itemList" :onDelete="onDelete" />
      <div v-if="itemList.length === 0" class="bg-blue p-2 text-white">
        Herhangi bir ürün yoktur.
      </div>
      <small
        class="mt-2 text-blue d-flex justify-content-end align-items-center"
        >{{ itemCount }} adet alınacak ürün vardır</small
      >
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AddSection from "@/components/AddSection";
import BuyList from "@/components/BuyList";
export default {
  name: "App",
  data() {
    return {
      itemList: [],
    };
  },
  methods: {
    onSave(e) {
      const saveObj = {
        title: e.target.value,
        createdAt: new Date().getTime(),
        completed: false,
      };
      axios
        .post("http://localhost:3000/items", saveObj)
        .then((save_response) => {
          e.target.value = "";
          e.target.focus();
          this.itemList.push(save_response.data);
          console.log(save_response);
        });
    },
    onDelete(item) {
      axios
        .delete(
          `http://localhost:3000/items/${item.id}
`
        )
        .then((res) => {
          console.log(res);
          this.itemList = this.itemList.filter((el) => el.id !== item.id);
        });
    },
  },
  computed: {
    itemCount() {
      return this.itemList.length;
    },
  },
  mounted() {
    axios.get(" http://localhost:3000/items").then((res) => {
      this.itemList = res.data || [];
      console.log(this.itemList);
    });
  },
  components: {
    BuyList,
    AddSection,
  },
};
</script>

<style></style>
