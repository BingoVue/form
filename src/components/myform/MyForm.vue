<template>
  <div>
    <slot></slot>
  </div>
</template>
<script>
export default {
  name: 'MyForm',
  props: {
    model: {
      type: Object,
      required: true
    },
    rules: {
      type: Object
    }
  },
  methods: {
    validate(cb){
      // 调用所有myformitem的validate，只要一个失败就失败
      // 此处得到一个promise数组，是所有form-item执行校验的结果集
      const validateResults = this.$children
        .filter(item=>!!item.prop)  // 留下带prop属性的项
        .map(item=>item.validate())

      // 判断所有结果
      Promise.all(validateResults)
        .then(()=>cb(true))
        .catch(()=>cb(false))
    }
  },
  provide(){
    return {
      form: this
    }
  }
}
</script>