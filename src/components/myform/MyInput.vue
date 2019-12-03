<template>
  <!-- input事件处理，实现双向绑定 -->
  <div><input :type="type" :value="value" @input="onInput" v-bind="$attrs"></div>
</template>
<script>
export default {
  inheritAttrs: false,
  name: 'MyInput',
  props: {
    type: {
      type: String,
      default: "text"
    },
    value: {
      type: String,
      default: ""
    }
  },
  methods: {
    onInput(e){
      // 遵循单向数据流原则，这里转发事件即可
      this.$emit('input', e.target.value)

      // 通知校验
      this.$parent.$emit('validate')
    }
  }
}
</script>