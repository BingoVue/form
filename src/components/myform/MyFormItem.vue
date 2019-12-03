<template>
  <div>
    <!-- label -->
    <label v-if="label">{{label}}</label>
    <!-- 表单元素 -->
    <slot></slot>
    <!-- 错误信息 -->
    <p class="error" v-if="error">{{error}}</p>
    <!-- {{form.rules[prop]}} -->
  </div>
</template>
<script>
import Schema from 'async-validator'
export default {
  name: 'MyFormItem',
  inject: ['form'],
  props: {
    label: {
      type: String,
      default: ''
    },
    prop: {
      type: String
    }
  },
  data(){
    return {
      error: ''
    }
  },
  methods: {
    validate(){
      // 1.获取校验规则和当前值
      const rule = this.form.rules[this.prop]
      const value = this.form.model[this.prop]
      // 2.创建Schema实例
      const schema = new Schema({
        // [xxx]计算属性
        [this.props]: rule
      })
      // 3.使用该实例执行校验
      return schema.validate({
        [this.props]: value
      },errors=>{
        if(errors){
          this.error = errors[0].message
        }else{
          this.error = ""
        }
      })
    }
  },
  mounted(){
    this.$on('validate', ()=>{
      this.validate()
    })
  }
}
</script>
<style>
  .error{
    color: red;
  }
</style>