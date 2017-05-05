<template>
  <div id="app">
    <Header></Header>
    <Comment></Comment>
    <Nav></Nav>
    <Trip></Trip>
    <Cost_statement></Cost_statement>
    <Notice></Notice>
    <Pay></Pay>
    <Advisory></Advisory>

  </div>
</template>

<script>
import Hello from './components/Hello'
import Header from './components/Header'
import Comment from './components/Comment'
import Nav from './components/Nav'
import Trip from './components/Trip'
import Cost_statement from './components/Cost_statement'
import Notice from './components/Notice'
import Pay from './components/Pay'
import Advisory from './components/Advisory'

export default {
  name: 'app',
  components: {
    Header,
    Comment,
    Nav,
    Trip,
    Cost_statement,
    Notice,
    Pay,
    Advisory
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
