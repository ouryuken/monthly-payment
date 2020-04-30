<template>
  <div id="app" class="container justify-center ">
    <div class="columns is-centered is-vcentered">
      <Table></Table>
    </div>
  </div>
</template>

<script>
import 'bulma/bulma.sass'
import Table from './components/table';

export default {
  name: 'App',
  components: {
    Table
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
