<template>
  <div>
    <h3>Todos</h3>
    <div class="legend">
      <span>Double click to mark as complete</span>
      <span>
        <span class="incomplete-box"></span> = Incomplete
      </span>
      <span>
        <span class="complete-box"></span> = Complete
      </span>
    </div>
    <div class="todos">
      <div @click="markTodo(todo)"  v-for="todo in allTodos" :key="todo.id" class="todo" v-bind:class="{'is-completed': todo.completed }">
        {{todo.title}}
        <i @click="deleteTodo(todo.id)" class="fas fa-trash-alt"></i>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'


export default {
  name: 'Todos',
  methods: {
    ...mapActions(['fetchTodos', 'deleteTodo', 'updateTodo']),
    markTodo(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed
      }
      this.updateTodo(updTodo)
    }
  },
  computed: mapGetters(['allTodos']),
  created() {
    this.fetchTodos()
  }
}
</script>

<style lang="scss" scoped>
  .todos {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1rem;
  }
  .todo {
    border: 1px solid #ccc;
    background: #41b883;
    padding: 1rem;
    border-radius: 5px;
    text-align: center;
    position: relative;
    cursor: pointer;
  }
  i {
    position: absolute;
    right: .5rem;
    bottom: .5rem;
    color: white;
    cursor: pointer;
  }
  .legend {
    display: flex;
    justify-content: space-around;
    margin-bottom: 1rem;
  }
  .complete-box {
    display: inline-block;
    width: 1rem;
    height: 1rem;
    background: #ccc;
  }
  .is-completed {
    background: #ccc;
    text-decoration: line-through;
    color: rgb(116, 116, 116);
  }
  .incomplete-box {
    display: inline-block;
    width: 1rem;
    height: 1rem;
    background: #41b883;
  }
  @media (max-width: 500px) {
    .todos {
      grid-template-columns: 1fr;
    }
  }

</style>
