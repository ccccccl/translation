<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 offset-3">


    <form class="form-inline" v-on:submit="submitText">
        <input class="form-control mr-sm-2" type="text" v-model="inputText" placeholder="输入要需要翻译的内容">
        <select class="form-control mr-sm-2" name="" v-model="lang">
            <option value="zh">中文</option>
            <option value="en">English</option>
            <option value="ja">Japanese</option>
            <option value="ko">Korean</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">
    </form>
    </div>
  </div>
</template>

<style>
    .form-inline{
        justify-content:center;
    }
</style>

<script>
export default{
    name: 'translateForm',
    data: function(){
        return {
            inputText: '',
            lang: 'en'
        }
    },
    methods: {
        submitText: function(e){
            this.$emit('formSubmit', this.inputText, this.lang)
            e.preventDefault()
        }
    }
}
</script>
