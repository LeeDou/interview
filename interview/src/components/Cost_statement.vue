<template>
  <div class="cost_statement">
    <a name="cost_statement"></a>
    <h1 class="hh" id="hh">费用说明</h1>
    <div class="pay_include">
      <h3>费用包含</h3>
      <ol>
      	<li>交通：行程中所列大巴车服务，行程中所列船票费用</li>
      	<li>餐饮：形成内所列餐食</li>
      	<li>服务人员：形成内所列餐食</li>
      	<li>保险：形成内所列餐食</li>
      	<li>其他费用：形成内所列餐食</li>
      </ol>
    </div>
    <div class="pay_include">
      <h3>费用不包含</h3>
      <ol>
      	<li>个人消费</li>
      	<li>餐饮费</li>
      	<li>个人消费及以上未提及的任何费用</li>
      </ol>
    </div>

  </div>

</template>

<script>
export default {
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
@import "../assets/style/cost_statement.scss"
</style>
