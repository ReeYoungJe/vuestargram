<template>
  <div :class="`${Fileter} filter-item`" :style="{ backgroundImage : `url(${imgData})` }"></div>
</template>

<script>

export default {
  name: "FilterBox",
  props:{
    imgData : String,
    Fileter : Array,
  },
}
</script>

<style scoped>
 @import "FilterBox.scss";
</style>