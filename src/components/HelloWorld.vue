<template>
  <div class="hello">
    <h1>傳情畫意</h1>
    <!-- <h3>題庫</h3> -->
    <!-- {{this.topic}} -->
    <!-- <div v-for="item in this.topic" :key="item.item">
      {{item.item}}
    </div> -->
    <img src="./../assets/boaz.png" alt="BOAZ">
    <hr>
    <div class="wrapper">
      <p>你的題目是:</p>
      <h4>{{this.result}}</h4>
    </div>
    <br>
    <!-- <button @click="randomTopic"><h1>Random Topic</h1></button> -->
    <button @click="randomTopic" type="button" class="btn" v-bind:class="{disable: this.count>1}">{{getCount()}}</button>
    <footer>AJA@2020 傳情畫意 v1.1</footer>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',  
  data() {
    return{
      topic: {},
      result: '',
      count:0
    }
  },
  methods:{
    getCount(){
      let val = this.count;
      if(val === 0){
        return '納命來'
      }else if(val === 1){
        return '太難了，再一次'
      }else{
        return '不能換了'
      }
    },
    randomTopic(){
      let result = Math.floor(Math.random() * this.topic.length);
      let final = "";
      for(let i =0; i<this.topic.length; i++){
        if(i== result){
          final = this.topic[i].item
          console.log(final);
          
        }
      }
      this.count ++;
      this.result = final
      console.log(this.count);
    }
  },
  mounted () {
    axios
      .get('https://script.googleusercontent.com/macros/echo?user_content_key=1j3v9XvmAWKq512en-LLDVpKw43zULn7TgXdljBBdRaLfOGNpeFB_YqZhyEBmPLMDto28QVzTMpjjuwCnmQehgwGVsXiD7Bjm5_BxDlH2jW0nuo2oDemN9CCS2h10ox_1xSncGQajx_ryfhECjZEnMtWSvurxVeV-K0dxmR31Gm-uOwAOgBYT1nsyRNU2dK0tVCJEe5wZjH3QZmleUkDXGX_kaSHpVtx&lib=MeGKzyIaPnJLaYAhkGPuAsIKA7t3_4itk')
      .then(response => (this.topic = response.data.user))
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
