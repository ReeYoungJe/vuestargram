<template>
  <div @click="fire" :class="`${changeFileter} filter-item`" :style="{ backgroundImage : `url(${imgData})` }">
    <span>{{Fileter}}</span>
  </div>
</template>

<script>

export default {
  name: "FilterBox",
  props:{
    imgData : String,
    Fileter : String,
    changeFileter : String,
  },
  methods:{
    fire(){
      this.emitter.emit('FilterName',this.Fileter)
    }
  }
}
</script>

<style scoped>
 @import "FilterBox.scss";
</style>