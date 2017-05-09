<template>
  <div id="app" class="app">
    <Top></Top>
    <Comment></Comment>
    <Navigation></Navigation>
    <Trip></Trip>
    <Cost_statement></Cost_statement>
    <Notice></Notice>
    <Pay></Pay>
    <Advisory></Advisory>

  </div>
</template>

<script>
import Hello from './components/Hello'
import Top from './components/Top'
import Comment from './components/Comment'
import Navigation from './components/Navigation'
import Trip from './components/Trip'
import Cost_statement from './components/Cost_statement'
import Notice from './components/Notice'
import Pay from './components/Pay'
import Advisory from './components/Advisory'


export default {
  name: 'app',
  components: {
    Top,
    Comment,
    Navigation,
    Trip,
    Cost_statement,
    Notice,
    Pay,
    Advisory
  }
}
</script>

<style lang="sass">
// @import "./assets/style/common.scss"
@import "./assets/style/app.scss"
// p{
//   background-color:green;
// }
// #app{
//   padding:0;
//   margin:0;
//   font-family: 'Avenir', Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }
</style>
