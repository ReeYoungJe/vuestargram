<template>
  <div>
    <div v-if="step === 0">
      <Post :InstarData="InstarData[i]" v-for="(InstarDataList, i) in InstarData" :key="InstarDataList"/>
    </div>

    <!-- 필터선택페이지 -->
    <div v-if="step === 1">
      <div class="upload-image" :style="{ backgroundImage : `url(${imgData})` }"></div>
      <div class="filters">
        <FilterBox :Fileter="Fileter"></FilterBox>
      </div>
    </div>


    <!-- 글작성페이지 -->
    <div v-if="step === 2">
      <div class="upload-image" :style="{ backgroundImage : `url(${imgData})` }"></div>
      <div class="write">
        <textarea class="write-box" @input="$emit('write', $event.target.value)">write!</textarea>
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
    FilterBox,
    Post: Post,
  },
  props: {
    InstarData: Object,
    step: Number,
    imgData : String,
  },
}
</script>

<style scoped>
 @import "Container.scss";
</style>