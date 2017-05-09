<template>
  <div class="navigation" >
    <a name="navigation"></a>
    <div class='nav_list'>
      <ul id="spot" v-on:mouseover="move('msg',$event)" >
        <li class="focus"><a href="#navigation" style="left:0">商品亮点</a></li>
        <li><a href="#trip" style="left:25%">行程安排</a></li>
        <li><a href="#cost_statement" style="left:50%">费用说明</a></li>
        <li><a href="#notice" style="left:75%">预定须知</a></li>
        <li class="list_span" id="list_span" style="left:0" ref='list_span'></li>
      </ul> 
    </div>
    <!-- <div class="border"></div> -->
    <div class="light">              
          <p>正统京都风味日式午餐，松阪牛料理</p>        
          <p>全程优选酒店，1晚正宗温泉享受</p>        
    </div>
    <div class="display">
    	<h1>“时尚东京，魅力大阪”</h1>
    	<img src="../assets/img/Bitmap@2x.png">
    	<p>在艾菲尔铁塔脚下的塞纳河码头边，登上装饰全透明玻璃窗的游船，用一个小时的时间欣赏两岸的极致美景。沿着塞纳河欣赏巴黎夜景中灯光璀璨的历史建筑，为您讲述璀璨巴黎的故事和法式生活。</p>
    </div>
  </div>

</template>

<script>
export default {
  data(){
    return {}
  },
  methods:{
    move: function(msg,event){
      let spot = this.$refs.list_span;
      let ev=event||window.event;
      let target = ev.target||ev.srcElement;
      let left1 =target.style.left;
      spot.style.left=left1;
      spot.style.transition="left 1s";
    }
  },
  created(){

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
@import "../assets/style/navigation.scss"


</style>
