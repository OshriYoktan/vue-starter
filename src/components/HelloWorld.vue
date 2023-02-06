<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div
      class="list"
      @click="$emit('deleteItem', item.id)"
      v-for="item in data"
      :key="item.id"
    >
      <router-link :to="item.id">{{ item.title }}</router-link>
      <p>Remove</p>
    </div>
    <button @click="addModal = !addModal">Add Item</button>
    <form @submit.prevent="$emit('addItem', newItem)"  v-if="addModal" class="add-item">
      <input type="text" v-model="newItem.title" placeholder="Enter Name..." />
      <button>Save</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
    data: Array,
  },
  data() {
    return {
      newItem: {id: '4', title: ''},
      addModal: false,
    };
  },
  methods: {
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.list {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin: 20px 0;
}

.list p {
  cursor: pointer;
}
</style>
