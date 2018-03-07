<template>
  <div id="translateForm" class="row">
    <div class="col-md-6 offset-3">
      <form id="transForm" class="well form-inline" v-on:submit="formSubmit">
        <input class="form-control" v-model="textToTranslate" type="text" placeholder="输入需要翻译的内容">
        <select class="form-control" v-model="language">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korea</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'translateForm',
    data: function () {
      return {
        textToTranslate: "",
        language: ''
      }
    },
    methods: {
      formSubmit: function (e) {
        //表单在submit事件触发后默认会刷新页面，此处阻止默认事件
        e.preventDefault();
//        alert(this.textToTranslate);
        this.$emit('translate', this.textToTranslate, this.language)
      },
    },
    //无需调用，自动执行
    created:function () {
      this.language='en';
    }
  }
</script>

<style>
  #transForm{
    border:1px #ccc solid;
    -webkit-border-radius:10px;
    -moz-border-radius:10px;
    border-radius:10px;
  }
</style>
