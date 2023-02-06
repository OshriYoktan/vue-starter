<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div class="item" v-for="item in currItem" :key="item.id">
      <p>Name: {{ item.title }}</p>
    </div>
  </div>
</template>

<script>
import { dataService } from '../services/dataService';

export default {
  data() {
    return {
      id: this.$route.params.id,
      data: dataService.getData(),
      currItem: null,
    }
  },
  methods: {

  },
  created() {
    this.currItem = this.data.filter(item => item.id === this.id)
  }

}
</script>

<style>

</style>