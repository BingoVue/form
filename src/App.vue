<template>
  <div id="app">
    <div class="element-ui-form"><ElementForm/></div>
    <div class="my-form"><MyForm/></div>
  </div>
</template>

<script>
import ElementForm from './components/ElementForm.vue'
import MyForm from './components/myform'
// import 

export default {
  name: 'app',
  components: {
    ElementForm,
    MyForm
  }
}
</script>
<style>
  .element-ui-form{
    padding: 0 20px;
    width: 40%;
    text-align: center;
    float: left;
  }
  .my-form{
    float: right;
    padding: 0 20px;
    width: 40%;
    text-align: center;
  }
</style>
