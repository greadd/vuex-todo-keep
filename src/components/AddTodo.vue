<template>
  <div>
    <h3>Add Todo</h3>
    <div class="add">
      <form @submit.prevent="onSubmit">
        <input type="text" v-model="title" placeholder="New todo...">
        <input type="submit" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import {mapActions} from 'vuex'
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    ...mapActions(['addTodo']),
    onSubmit() {
      this.addTodo(this.title)
    }
  }

}
</script>


<style lang="scss" scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    border: 1px solid #41b883;
    padding: 0.5rem;
    outline: none;
  }
  input[type="submit"] {
    flex: 2;
    background: #41b883;
    color: #Fff;
    border: 1px solid #41b883;
    cursor: pointer;
  }

</style>
