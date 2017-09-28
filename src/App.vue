<template>
  <div class="text-center" id="app">
    <h1>Word Translator</h1>
    <h5>Powered By Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>


  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170723T033042Z.51988b33e0c20fa4.0b07c6a87a3e5f02d8280de3b53434601dd26f38&lang='+language+'&text='+text)
.then((response) => {
  this.translatedText = response.body.text[0];
});


    }
  }
}
</script>

<style>
body {
  background:#fefefe;

}
</style>
