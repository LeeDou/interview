<template>
  <div ref="root" style="user-select: none;-webkit-user-select: none;overflow: hidden">
    <div  class="sliderPanel"
          :class="{transitionAni:ani}"
          :style="{height:height,transform:translateX}">
      <div v-for="item in itemList" class="picbox" :style="{left:item.x+'px'}">
        <!-- <img  :style="{width:width,top:top}"  :src="item.url" > -->
        <img  class="box"  :src="item.url" style="height:100%">
      </div>
    </div>


    <!-- <div class="test"><img src="../assets/img/logo.png" alt=""></div> -->
  </div>
</template>
<script>
  const SCREEN_WIDTH=document.body.clientWidth
  const SCREEN_HEIGHT=document.body.scrollHeight/5
  var left,center,right
  var selectIndex=0
  var count=0
  var second=3//slider 时间间隔
  var timer=null
  var ani=null
  var debugScale=1.0//测试用可调整为小于1
  var Direction={left:'left',right:'right'};
  var autoDirection=Direction.right
  var canClick=true
  export default({
    data:function(){
      return{
        width:'100%',
        height:SCREEN_HEIGHT+'px',
        top:0,
        ani:true,
        translateX:'scale('+debugScale+') translateX(0px)',
        imgArray:[
          {
            x:0,
            title1:'现在，在您的实验室',
            url:require("../assets/img/Mask.png"),
            selected:false,
          },
          {
            x:0,
            title1:'Sequel开启新基因组时代',
            url:require("../assets/img/Bitmap.png"),
          },
          {
            x:0,
            title1:'BRCA1/2全外显子基因突变检测',
            url:require("../assets/img/Bitmap.png"),
          },
          {
            x:0,
            title1:'现在，在您的实验室',
            url:require("../assets/img/Bitmap.png"),

          },
          {
            x:0,
            title1:'现在，在您的实验室',
            url:require("../assets/img/Bitmap.png"),
          },
          {
            x:0,
            title1:'现在，在您的实验室',
            url:require("../assets/img/Bitmap.png"),
          }
         
        ],
        itemList:[]
      }
    },
    mounted:function(){
      ani=this.$refs.root.querySelector('.sliderPanel')
      count=this.imgArray.length
      this.setIndex(selectIndex)
      //自动滚动切换图片
      this.slideAuto(second)
    },
    methods:{
      // clickLeft:function(){
      //     if(!canClick) return false
      //   autoDirection=Direction.left
      //   this.slideAuto(second)
      //   this.moveLeftAni()
      //   canClick=false
      // },
      // clickRight:function(){
      //   if(!canClick) return false
      //   autoDirection=Direction.right
      //   this.slideAuto(second)
      //   this.moveRightAni()
      //   canClick=false
      // },
      slideRight:function () {
        selectIndex++
        if(selectIndex+1>count){
          selectIndex=0
        }else if(selectIndex<0){
          selectIndex=count-1
        }
        this.setIndex(selectIndex)
      },
      // slideLeft:function () {
      //   selectIndex--
      //   if(selectIndex+1>count){
      //     selectIndex=0
      //   }else if(selectIndex<0){
      //     selectIndex=count-1
      //   }
      //   this.setIndex(selectIndex)
      // },
      // clickSliderCircle:function (index) {
      //   this.slideAuto(second)
      //   this.setIndexPre(index)
      // },
      setIndexPre:function (index) {
        if(!canClick) return false
        canClick=false
        if(index==selectIndex)return
        var leftIndex=index
        var centerIndex=selectIndex
        var rightIndex=index
        for(var i=0;i<count;i++){
          if(i==selectIndex){
            this.imgArray[i].selected=true
          }else{
            this.imgArray[i].selected=false
          }
        }
        left=this.imgArray[leftIndex]
        center=this.imgArray[centerIndex]
        right=this.imgArray[rightIndex]
        left=JSON.parse(JSON.stringify(left))
        right=JSON.parse(JSON.stringify(right))
        left.x=-SCREEN_WIDTH
        center.x=0
        right.x=SCREEN_WIDTH
        left.index=leftIndex
        center.index=centerIndex
        right.index=rightIndex
        this.itemList=[left,center,right]
        if(index>selectIndex){
          autoDirection=Direction.right;
            +function(obj){
            obj.anicompted(
              'scale('+debugScale+') translateX('+0+'px)',
              'scale('+debugScale+') translateX('+-SCREEN_WIDTH+'px)',
              function(){
                obj.setIndex(index)
              })
          }(this)
          //右移
        }else if(index<selectIndex){
          //左移
          autoDirection=Direction.left;
          +function(obj){
            obj.anicompted(
              'scale('+debugScale+') translateX('+0+'px)',
              'scale('+debugScale+') translateX('+SCREEN_WIDTH+'px)',
              function(){
                obj.setIndex(index)
              })
          }(this)
        }
      },
      setIndex:function (index) {
        var leftIndex=index-1
        var centerIndex=index
        var rightIndex=index+1
        if(index<=0){
          index=0
          leftIndex=count-1
          centerIndex=index
          rightIndex=index+1
        }else if(index>=count-1){
          index=count-1
          leftIndex=index-1
          centerIndex=index
          rightIndex=0
        }
        selectIndex=index
        for(var i=0;i<count;i++){
            if(i==selectIndex){
              this.imgArray[i].selected=true
            }else{
              this.imgArray[i].selected=false
            }
        }
        left=this.imgArray[leftIndex]
        center=this.imgArray[centerIndex]
        right=this.imgArray[rightIndex]
        left.x=-SCREEN_WIDTH
        center.x=0
        right.x=SCREEN_WIDTH
        left.index=leftIndex
        center.index=centerIndex
        right.index=rightIndex
        this.itemList=[left,center,right]
      },
      slideAuto:function () {
          clearInterval(timer);
          +function (obj) {
            timer=setInterval(function () {
              if(autoDirection==Direction.left){
                obj.moveLeftAni()
              }else{
                obj.moveRightAni()
              }
            },second*1000)
          }(this)
      },
      moveLeftAni:function(){
          +function(obj){
            obj.anicompted(
              'scale('+debugScale+') translateX('+0+'px)',
              'scale('+debugScale+') translateX('+SCREEN_WIDTH+'px)',
              function(){
                obj.slideLeft()
              })
          }(this)
      },
      moveRightAni:function(){
        +function(obj){
            obj.anicompted(
              'scale('+debugScale+') translateX('+0+'px)',
              'scale('+debugScale+') translateX('+-SCREEN_WIDTH+'px)',
              function(){
                obj.slideRight()
              })
          }(this)
      },
      anicompted:function(fromStr,toStr,callBack){
        var handler=null,obj=this
        handler=function(){
          ani.removeEventListener('webkitTransitionEnd',handler,false)
          callBack()
          obj.ani=false
          obj.translateX=fromStr
          canClick=true
        }
        ani.removeEventListener('webkitTransitionEnd',handler,false)
        ani.addEventListener('webkitTransitionEnd',handler,false)
        this.ani=true
        this.translateX=toStr
      }
    }

  })

</script>
<style scoped>
  .transitionAni{
    transition: all 0.8s cubic-bezier(.23,1,.32,1);
  }

  .picbox{
    width: 100%;
    position: absolute;
    top: 0;
    overflow: hidden;
    transition: all 0.45s ease;
  }
  /*.picbox img{
    width: 100%;
    height: 200px;
  }*/
/*  .test{
    clear: both;
    position: absolute;

    width: 100%;
  }*/
 /* .sliderPanel{
    width: 100%;
    /*height: 200px;*/
  /*}*/
 /* .sliderPanel img{
    width: 100%;
  }*/
  .box{
    width: 100%;
  }
 
  
 
</style>