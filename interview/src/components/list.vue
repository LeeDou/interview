<template>  
  <div class="slide">  
    <swiper :options="swiperOption"  ref="mySwiper">  
      <!-- 这部分放你要渲染的那些内容 -->  
      <swiper-slide v-for="item in items">
        <img :src="item.url" alt="item.title">   
      </swiper-slide>  
      <!-- 这是轮播的小圆点 -->  
      <div class="swiper-pagination" slot="pagination"></div>  
    </swiper>  
  </div>  
</template>  
<script>  
import { swiper, swiperSlide } from 'vue-awesome-swiper'  
export default {  
  components: {  
    swiper,  
    swiperSlide  
  },  
  data() {  
    return {  
      swiperOption: {  
        notNextTick: true,  
        pagination: '.swiper-pagination',  
        slidesPerView: 'auto',  
        centeredSlides: true,  
        paginationClickable: true,  
        spaceBetween: 30,  
        onSlideChangeEnd: swiper => {  
        //这个位置放swiper的回调方法  
          this.page = swiper.realIndex+1;  
          this.index = swiper.realIndex;  
        }  
    },
    items:[
      {
        title:'这是一张展示图片',
        url:require("../assets/img/Mask@3x.png"),
      },
      {
        title:'这是一张展示图片',
        url:require("../assets/img/Bitmap@3x.png"),
      },
      {
        title:'这是一张展示图片',
        url:require("../assets/img/Mask@3x.png"),
      }
    ]
                            
    }  
  },  
  //定义这个sweiper对象  
  computed: {  
    swiper() {  
      return this.$refs.mySwiper.swiper;  
    }  
  },  
  mounted () {   
    this.swiper.slideTo(0, 0, false);  
  }  
}  
</script>  
<style  scoped> 
  .slide{
    width: 100%;

  }  
  .slide img{
      width: 100%;
  }  
</style> 
