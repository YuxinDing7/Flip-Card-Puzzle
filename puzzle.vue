<template>
<div class="puzzle-container">
  <flip-card v-for="i in 20" :frontColor="flipCardInfo[i-1].frontColor" :backColor="flipCardInfo[i-1].backColor" :title="flipCardInfo[i-1].title" :content="flipCardInfo[i-1].content" @click="loveYou(i)" ref="flipCardsRefs"/>
</div>

</template>

<script setup>
import FlipCard from "./flip-card.vue"
import { ref } from 'vue'
const flipCardsRefs=ref([])
var backColor1 = ref("#dfca7f")
var backColor2 = ref("#cfde89")
var backColor3 = ref("#e6b379")
var backColor4 = ref("#e99779")
const flipCardInfo = ref([
{frontColor:"#e6fe72",backColor:"#cfde89", title:"生日", content:"2003/08/22"},
{frontColor:"#e6fe72",backColor:backColor2, title:"家乡", content:"江苏无锡"},
{frontColor:"#e6fe72",backColor:"#cfde89", title:"目前方向", content:"前端开发"},
{frontColor:"#e6fe72",backColor:backColor2, title:"本科", content:"华南理工"},
{frontColor:"#e6fe72",backColor:"#cfde89", title:"专业", content:"人工智能"},
{frontColor:"#fee587",backColor:backColor1, title:"喜欢的运动", content:"散步"},
{frontColor:"#fee587",backColor:backColor1, title:"喜欢的动画", content:"东京残响 亚人"},
{frontColor:"#fee587", backColor:backColor1, title:"最爱的人", content:"轩", click:"loveYou"},
{frontColor:"#fee587", backColor:backColor1, title:"喜欢的颜色", content:"粉色"},
{frontColor:"#fee587", backColor:backColor1, title:"喜欢的游戏", content:"Apex 塞尔达 动物森友会 喷射战士"},
{frontColor:"#feb45a", backColor:"#e6b379", title:"印象最深的电影", content:"时时刻刻"},
{frontColor:"#feb45a", backColor:backColor3, title:"印象最深的歌", content:"スウィートソウル"},
{frontColor:"#feb45a", backColor:backColor3, title:"印象最深的作家", content:"芥川龙之介 维克多·雨果 森见登美彦"},
{frontColor:"#feb45a", backColor:backColor3, title:"印象最深的城市", content:"京都"},
{frontColor:"#feb45a", backColor:"#e6b379", title:"印象最深的画", content:"毒气战--萨金特"},
{frontColor:"#fea17c", backColor:"#e99779", title:"曾经的梦想", content:"当一个建筑师，设计一家在山中的民宿"},
{frontColor:"#fea17c", backColor:"#e99779", title:"想去旅游的地方", content:"新疆"},
{frontColor:"#fea17c", backColor:backColor4, title:"想定居的城市", content:"无锡"},
{frontColor:"#fea17c", backColor:"#e99779", title:"曾经的梦想", content:"……"},
{frontColor:"#fea17c", backColor:"#e99779", title:"喜欢的专辑", content:"Blurryface Communion"},
])

function loveYou(j)
{
  if(j==8) //点击“最爱的人”时才触发
  {
    console.log('进入')
    backColor1.value="#ff66a3"
    backColor2.value="#ff66a3"
    backColor3.value="#ff66a3"
    backColor4.value="#ff66a3" //把爱心处的卡片背面都变成粉色
    for (var i=0; i < flipCardsRefs.value.length; i++){
      flipCardsRefs.value[i].flip() //把卡片全部翻转
    }
    setTimeout(() => {
      for (var i=0; i < flipCardsRefs.value.length; i++){
        flipCardsRefs.value[i].flipBack()
        backColor1.value="#dfca7f"
        backColor2.value="#cfde89"
        backColor3.value="#e6b379"
        backColor4.value="#e99779"
      }
    }, 2000); //2秒后翻转回来，把卡牌背面的颜色变回原来的
  }

} 
</script>

<style>
.puzzle-container{
  display: grid;
  grid-template-columns: repeat(5,100px);
  grid-template-rows: repeat(4,120px);
  row-gap: 8px;
  column-gap: 8px;
}
</style>