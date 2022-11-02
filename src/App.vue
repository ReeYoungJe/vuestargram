<template>
  <div class="header" style="position: relative">
    <ul class="header-button-left">
      <li @click="cancel();">Cancel</li>
    </ul>
    <ul class="header-button-right">
      <li v-if="step === 1" @click="next();">Next</li>
      <li v-if="step === 2" @click="publish();">발행</li>
    </ul>
    <h2 style="position: absolute; left: 50%; transform: translate(-50%); font-size:17px; " >VueStaGram</h2>
  </div>
  <Container :changeFileter="changeFileter"  @write="text = $event" :imgData="imgData" :InstarData="InstarData" :step="step" />

  <div v-if="step === 0">
    <button class="more"  @click="more">더보기</button>

  </div>
  <div class="footer" v-if="step === 0" >
    <ul class="footer-button-plus">
      <input @change="upload" type="file" id="file" class="inputfile"/>
      <label for="file" class="input-plus">+</label>
    </ul>
  </div>


</template>

<script>

import Container from "@/components/Container";
import InstarData from "@/assets/InstarData";
import axios from 'axios'

export default {
  name: 'App',
  data(){
    return{
      InstarData : InstarData,
      count : 0,
      step : 0,
      imgData : '',
      text :'',
      changeFileter :'',
    }
  },
  mounted(){
    this.emitter.on('FilterName' , (a)=>{
      this.changeFileter = a;
    });
  },
  components: {
    Container: Container,
  },
  methods: {

    more() {
      axios.get(`https://codingapple1.github.io/vue/more${this.count}.json`)
          .then((show) => {
            this.InstarData.push(show.data)
            this.count++;
          })
          .catch(() => {
            alert('마지막 게시물 입니다.')
          })

    },
    publish(){
      var InstarData = {
        name: "User Name",
        userImage:  this.imgData,
        postImage:  this.imgData,
        likes: 36,
        date: "May 15",
        liked: false,
        content: this.text,
        filter: "perpetua"
      };
      this.InstarData.unshift(InstarData);
      this.step = 0
    },
    next(){
      this.step ++
    },
    cancel(){
      this.step = 0
    },
    upload(e){
      let  file = e.target.files;
      let url = URL.createObjectURL(file[0]);
      this.imgData = url
      this.step ++;
    }
  },
}
</script>

<style>
body {
  margin: 0;
}

ul {
  padding: 5px;
  list-style-type: none;
}

.logo {
  width: 22px;
  margin: auto;
  display: block;
  position: absolute;
  left: 0;
  right: 0;
  top: 13px;
}

.header {
  width: 100%;
  height: 40px;
  background-color: white;
  padding-bottom: 8px;
  position: sticky;
  top: 0;
}

.header-button-left {
  color: skyblue;
  float: left;
  width: 50px;
  padding-left: 20px;
  cursor: pointer;
  margin-top: 10px;
}

.header-button-right {
  color: skyblue;
  float: right;
  width: 50px;
  cursor: pointer;
  margin-top: 10px;
}

.footer {
  width: 100%;
  position: sticky;
  bottom: 0;
  padding-bottom: 10px;
  background-color: white;
}

.footer-button-plus {
  width: 80px;
  margin: auto;
  text-align: center;
  cursor: pointer;
  font-size: 24px;
  padding-top: 12px;
}

.sample-box {
  width: 100%;
  height: 600px;
  background-color: bisque;
}

.inputfile {
  display: none;
}

.input-plus {
  cursor: pointer;
}

#app {
  box-sizing: border-box;
  font-family: "consolas";
  margin-top: 60px;
  width: 100%;
  max-width: 460px;
  margin: auto;
  position: relative;
  border-right: 1px solid #eee;
  border-left: 1px solid #eee;
}
.more{
  width:100%;
  border:0px solid;
  background-color: deepskyblue;
  padding-top:20px;
  padding-bottom:20px;
}
</style>
