<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:translate="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  components: {
    TranslateForm,TranslateOutput//组件在此处声明后才能使用
  },
  data:function () {
    return {
        translatedText:''
    }
  },
  methods:{
      translateText:function (text,language) {
//        alert(text);
        var key='trnsl.1.1.20180131T132401Z.d7aa13ba53afe5ca.787118c1b2751d6f836ad0db17e35e562b01076b',
          text=text,
          formate='',
          callback='';
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key='+key
        +'&text='+text
        +'&lang='+language
        ).then((responce)=>{
//            console.log(responce)
          this.translatedText=responce.body.text[0];
        });
      }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
