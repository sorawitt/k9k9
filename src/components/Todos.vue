<template>
<div>
<h1>"TODOS TODOS TODOS"</h1>
<div v-bind:key="todo.id" v-for="todo in todos">
  <h3>{{ todo.title }} </h3>
</div>
</div>
</template>

<script>
export default {
  name: "Todos",
  props: ["todos"]
}
</script>

<style scoped>

</style>

