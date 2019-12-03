<template>
  <div>
    <h3>Element UI Form</h3>
    <el-form :model="user" :rules="rules" ref="elForm">
      <el-form-item label="姓名" prop="username">
        <el-input v-model="user.username"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input type="password" v-model="user.password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button @click="submitForm('elForm')">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import {Form, FormItem, Input, Button} from 'element-ui'
export default {
  name: 'ElementForm',
  components:{
    'el-form': Form,
    'el-form-item': FormItem,
    'el-input': Input,
    'el-button': Button
  },
  data(){
    return {
      user: {
        username: "Bingo",
        password: '123456'
      },
      rules: {
        username: [{required: true, message: '请输入姓名'}],
        password: [{required: true, message: '请输入密码'}]
      }
    }
  },
  methods: {
    submitForm(formName){ // 表单提交时候校验
      this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('校验成功！');
          } else {
            alert('校验失败！');
          }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
