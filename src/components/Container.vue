<template>
  <div>
    <Post :InstarData="InstarData[i]" v-for="(InstarDataList, i) in InstarData" :key="InstarDataList" />
  </div>
</template>

<script>
import Post from "@/components/Post";
export default {
  name: "Container",
  components: {
    Post : Post,
  },
  props : {
    InstarData : Object,
  }

}
</script>

<style scoped>

</style>