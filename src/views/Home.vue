<template>
  <div class="home">
    <HelloWorld @addItem="addNewItem" @deleteItem="handleDelete" :data="this.data" msg="Sup" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import { dataService } from "../services/dataService";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  data() {
    return {
      data: dataService.getData(),
    };
  },
  methods: {
    handleDelete(id) {
      const newData = this.data.filter(item => item.id !== id)
      this.data = newData
    }, 
    addNewItem(newItem) {
      this.data.push(newItem)
    }

  },
  mounted() {},
};
</script>

