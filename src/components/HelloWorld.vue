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
    <h3>結果: {{this.result}}</h3>
    <br>
    <!-- <button @click="randomTopic"><h1>Random Topic</h1></button> -->
    <button @click="randomTopic" type="button" class="btn btn-light">Random Topic</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',  
  data() {
    return{
      topic: {},
      result: ''
    }
  },
  methods:{
    randomTopic(){
      let result = Math.floor(Math.random() * this.topic.length);
      let final = "";
      for(let i =0; i<this.topic.length; i++){
        if(i== result){
          final = this.topic[i].item
          console.log(final);
          
        }
      }
      this.result = final
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
