<template>
  <section class="banner">
    <input class="search" type="text" placeholder="输入商家名、菜品" @keyup.enter="sendData" />
    <img src="../assets/img/Mask.png" alt="搜索" @click="sendData" />
  </section>
</template>
<style lang="sass">
  .banner{
    width:100%;
    height:186px;
    background-image: url("../assets/img/Mask.png");
    background-repeat: no-repeat;
    background-size: 100% 186px;
    text-align: center;
    position: relative;
    .search{
      width:80%;
      height: 30px;
      line-height: 30px;
      border-radius: 15px;
      border: none;
      margin-top: 6px;
      text-align: center;
      background-color: #f7f4f4;
    }
  img{
    position: absolute;
    /* left: 20px; */
    width: 25px;
    height: 25px;
    right: 46px;
    top: 10px;
  }
  }
</style>
<script>
  export default {
    data() {
      return {
       /* keyword: ""*/
      }
    },
    methods: {
      sendData: function() {
        let keyword;
        keyword = $('.search').val();
        console.log(keyword);
        this.$http.get('', {"keyword": keyword});
      },
      scrollB: function () {

      }
    },
   created() {
      console.log("sc");

     let timer = null;
     clearInterval(timer);
     timer = setInterval(function () {
       move();
     }, 5000);
     let curIndex=0;
     let bgImg = ['Mask.png', 'Mask.png', 'Mask.png'];
     let len = bgImg.length;
     function move() {
         if(curIndex == len-1){
           curIndex = 0;
         }else{curIndex += 1;}
       $('.banner').css("background-image","url(/static/img/" + bgImg[curIndex] + ")");
     }
    },
  }
</script>
