<template>
  <div>
    <h3>My Form</h3>
    <my-form :model="user" :rules="rules" ref="myForm">
      <my-form-item label="姓名" prop="username">
        <my-input placeholder="请输入姓名" v-model="user.username"/>
      </my-form-item>
      <my-form-item label="密码" prop="password">
        <my-input type="password" placeholder="请输入密码" v-model="user.password"/>
      </my-form-item>
      <my-form-item>
        <button @click="submitLogin('myForm')">提交</button>
      </my-form-item>
    </my-form>
  </div>
</template>
<script>
import MyInput from './MyInput'
import MyFormItem from './MyFormItem'
import MyForm from './MyForm'
export default {
  name: 'MyElementForm',
  data(){
    return {
      user: {
        username: 'Bingo',
        password: '123456'
      },
      rules: {
        username: [{required: true, message: '请输入姓名'}],
        password: [{required: true, message: '请输入密码'}]
      }
    }
  },
  methods: {
    submitLogin(formName){
      this.$refs[formName].validate((isValidate)=>{
        if (isValidate) {
          alert('校验成功！');
        } else {
          alert('校验失败！');
        }
      })
    }
  },
  components: {
    'my-input': MyInput,
    'my-form-item': MyFormItem,
    'my-form': MyForm
  }
}
</script>