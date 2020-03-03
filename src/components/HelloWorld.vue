<template>
  <div class="hello">
    <h1>傳情畫意</h1>
    <!-- <h3>題庫</h3> -->
    <!-- <div v-for="item in topic" :key="item">
      {{item}}
    </div> -->
    <hr>
    <h3>結果: {{this.result}}</h3>
    <button @click="randomTopic"><h1>Random Topic</h1></button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return{
      topic: ['習近平','金正恩','耿爽','小虎隊','館長','隱形人','洪金寶','scrum of scrum','紫禁之巔','夜市人生','寄生上流','R&R','拉斯維加斯','韓國','路易莎','婚宴蟑螂'],
      result: ''
    }
  },
  methods:{
    randomTopic(){
      let result = Math.floor(Math.random() * this.topic.length);
      console.log(this.topic[result]);
      this.result = this.topic[result];
    }
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
