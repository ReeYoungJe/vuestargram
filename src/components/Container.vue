<template>
  <div>
    <Post :InstarData="InstarData[0]" />
    <Post :InstarData="InstarData[1]" />
    <Post :InstarData="InstarData[2]" />


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
    InstarData : Array,
  }

}
</script>

<style scoped>

</style>