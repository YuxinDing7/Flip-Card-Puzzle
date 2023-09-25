<template>
    <div class="flip-card">
      <div :class="[{completelyFlip:isActive}, commonClass]">
        <!--commonClass对应平时的style：仅在鼠标停留在其上面时翻转；completelyFlip对应展示爱心时的style：完全维持翻转-->
        <div class="flip-card-front" :style="{backgroundColor:frontColor,}">
            <h4>{{ title }}</h4>
        </div>
        <div class="flip-card-back" :style="{backgroundColor:backColor,}">
          <li v-for="item in content.split(' ')">
            <h4>{{ item }}</h4>
          </li>
        </div>
      </div>
    </div>
</template>
    
<script setup>
import { ref } from 'vue'
var isActive = ref(false)
const commonClass = ref("flip-card-inner")
const props = defineProps({
  title:{
      type:String,
      default:"主标题"
  },
  subtitle:{
      type:String,
      default:"副标题"
  },
  content:{
      type:String,
      default:"内容"
  },
  frontColor:{
    type:String,
    default: "#fff"
  },
  backColor:{
    type:String,
    default: "#fff"
  },
})

function flip(){
  isActive=ref(true)
}

function flipBack(){
  isActive=ref(false)
}

defineExpose({flip,flipBack})
</script>
    
<style scoped>
  /* 翻转卡片容器 - 将宽度和高度设置为您想要的任何值。 我们添加了边框属性来演示翻转本身在悬停时会脱离盒子（如果您不想要 3D 效果，请删除透视 */
  .flip-card {
    background-color: transparent;
    width: 100px;
    height: 120px;
    perspective: 1000px; /* 如果您不想要 3D 效果，请删除它 */
  }
  
  /* 需要这个容器来定位正反面 */
  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }
  
  .completelyFlip
  {
    transform: rotateY(180deg);
  }

  /* 将鼠标移到翻转框容器上时进行水平翻转 */
  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }
  
  /* 定位正面和背面 */
  .flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden; /* Safari */
    backface-visibility: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  
  /* 设置正面的样式（如果图像丢失则回退）*/
  .flip-card-front {
    background-color: #5ea1d2;
    color: black;
  }
  
  /* 为背面设置样式 */
  .flip-card-back {
    background-color: rgb(255, 152, 234);
    color: white;
    transform: rotateY(180deg);
  }

  h4{
    padding: 4px 10px;
    margin: 0px 0px;
  }
  </style>