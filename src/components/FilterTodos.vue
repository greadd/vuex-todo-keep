<template>
  <div>
    Filter todos:
    <select @change="filterTodos($event.target.value)">
      <option value="100">100</option>
      <option value="50">50</option>
      <option value="10">10</option>
      <option value="5">5</option>
    </select>
  </div>
</template>

<script>
import {mapActions} from 'vuex'
export default {
  name: 'FilterTodos',
  methods: {
    ...mapActions(['filterTodos'])
  }
}
</script>

<style scoped>
  select {
    margin-top: 1rem;
    padding: .5rem;
    border: 1px solid #41b883;
  }
</style>
