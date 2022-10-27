<template>

  <div class="post">
    <div class="post-header">
      <div class="profile"></div>
      <span class="profile-name">{{InstarData.name}}</span>
    </div>
    <div class="post-body" :style="{ backgroundImage : 'url(' + InstarData.postImage +')' }"></div>
    <div class="post-content">
      <p>{{InstarData.likes}} Likes</p>
      <p><strong>{{InstarData.name}}</strong> {{InstarData.concat}}</p>
      <p class="date">May 15</p>
    </div>
  </div>



</template>

<script>
export default {
  name: "Post",
  props : {
    InstarData : Array,
  }
}
</script>

<style scoped>
@import "Post.scss";
</style>