<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm @formSubmit="translate"></translateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
  import Vue from 'vue'
  import TranslateForm from './components/Form'
  import TranslateOutput from './components/Output'

  export default {
    name: 'app',
    data: function () {
      return {
        translatedText: ''
      }
    },
    components: {TranslateForm, TranslateOutput},
    props: ['inputText'],
    methods: {
      translate: function (text, lang) {
        //this.inputText = text
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181218T083357Z.a97f0215dd5ba225.be5ca006b69ef925c16f319e557432f021ab5b24&text=' + text + '&lang=' + lang)
          .then((response) => {
            this.translatedText = response.body.text[0]
          })
      }
    }
  }
</script>

<style lang="scss">
  body{
    over-flow: hidden;
  }
  #app {
    padding: 50px 0;
    text-align: center;
  }

  #TranslateOutput {
    margin-top: 50px;
    font-size: 24px;
  }
</style>
