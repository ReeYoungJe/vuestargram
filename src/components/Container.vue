<template>
  <div>
    <div v-if="step === 0">
      <Post :InstarData="InstarData[i]" v-for="(InstarDataList, i) in InstarData" :key="InstarDataList"/>
    </div>

    <!-- 필터선택페이지 -->
    <div v-if="step === 1">
      <div :class="`${changeFileter} upload-image`" :style="{ backgroundImage : `url(${imgData})` }">
        {{changeFileter}}
      </div>
      <div class="filters">
        <FilterBox :imgData="imgData" :Fileter="Fileter" v-for="Fileter in Fileter" :key="Fileter"></FilterBox>
      </div>
    </div>


    <!-- 글작성페이지 -->
    <div v-if="step === 2">
      <div :class="`${changeFileter} upload-image`" :style="{ backgroundImage : `url(${imgData})` }"> {{changeFileter}}</div>
      <div class="write">
        <textarea class="write-box" @input="$emit('write', $event.target.value)" placeholder="내용을 작성 해주 세 욘"></textarea>
      </div>
    </div>

  </div>
</template>

<script>
import Post from "@/components/Post";
import FilterBox from "@/components/FilterBox";

export default {
  name: "Container",
  data(){
    return{
      Fileter: [ "aden", "_1977", "brannan", "brooklyn", "clarendon", "earlybird", "gingham", "hudson",
      "inkwell", "kelvin", "lark", "lofi", "maven", "mayfair", "moon", "nashville", "perpetua",
      "reyes", "rise", "slumber", "stinson", "toaster", "valencia", "walden", "willow", "xpro2"]
    }
  },
  components: {
    FilterBox : FilterBox,
    Post: Post,
  },
  props: {
    InstarData: Object,
    step: Number,
    imgData : String,
    changeFileter : String,

  },
}
</script>

<style scoped>
 @import "Container.scss";
</style>