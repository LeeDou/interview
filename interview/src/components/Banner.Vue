<template>  
  <div class="box">  
    <transition-group tag='ul' class="slide" name='image'>
      <li v-for='(image,index) in img' :key='index' v-show='index===mark'>
        <a><img :src="image.src"></a>
      </li>
    </transition-group>
    <div class="bullet">
            <span v-for='(item,index) in img.length' :class="{'active':index===mark}" @click='change(index)'></span>
        </div>
  </div>
</template>  
<script>  
 
export default {  
  data() {  
    return {  
      mark: 0,
      timer: null,
        img: [
          {
        	src:require("../assets/img/Mask@3x.png"),
        	title:'展示图片'
          },
          {
            src:require("../assets/img/Bitmap@3x.png"),
        	title:'展示图片'
          }, 
          {  
            src:require("../assets/img/Mask@3x.png"),
        	title:'展示图片'
          },
          {
            src:require("../assets/img/Bitmap@3x.png"),
        	title:'展示图片'
          }        
        ]
                            
    }  
  },  
  created() {
  	this.play()
  },
  methods:{
  	change(i){
      this.mark = i
  	},
  	autoPlay() {
  	  this.mark++
  	  if (this.mark === 4) {
  	  	this.mark = 0
  	  	return
  	  }	
  	},
  	play() {
  		setInterval(this.autoPlay,5000)
  	}
  },  
  computed: {  
    
  }  
  
}  
</script>  
<style lang="sass" scoped> 
@import "../assets/style/banner.scss"

// .box{
//     width: 100%;
//     height: 14rem;
//     margin: 0 auto;
//     zoom: 1;
//     overflow: hidden;
//     position: relative;
//     .slide {
// 	    width: 100%;
// 		li {
// 		    position: absolute;
// 		    width:100%;
// 		    img {
// 			    width:100%;           
// 			}
// 		}
// 	}
// 	.image-enter-active {
// 	    transform: translateX(0);
// 	    transition: all 1s ease;
// 	}
	        
// 	.image-leave-active {
// 	    transform: translateX(-100%);
// 	    transition: all 1s ease;
// 	}
	        
// 	.image-enter {
// 	    transform: translateX(100%)
// 	}
	        
// 	.image-leave {
// 	    transform: translateX(0)
// 	}
	      
// 	.bullet {
// 	    width: 100%;
// 	    position: absolute;
// 	    bottom: 0.6rem;
// 	    margin: 0 auto;
// 	    text-align: center;
// 	    z-index: 10;
// 	    span {
// 		    width: 1.2rem;
// 		    height: 0.3rem;
// 		    border:0.01rem solid;
// 		    background: white;
// 		    display: inline-block;
// 		    margin-right: 10px;
// 		}
		        
// 		.active {
// 		    background: red;
// 		}
// 	}
// }       

        

        

</style> 
