<template>
  <validate-form class="formLogin" @form-submit="onFormSubmit">
      <div class="mb-3">
        <label class="form-label">邮箱：</label>
        <validate-input ref="inputRef" :rules="emailRules" v-model="emailVal" placeholder="请输入" type="email"></validate-input>
        <div id="emailHelp" class="form-text" v-show="emailRules.error">{{emailRules.message}}</div>
      </div>
      <div class="mb-3">
        <label class="form-label">密码：</label>
        <validate-input :rules="passwordRules" v-model="passwordVal" placeholder="请输入" type="password"></validate-input>
        <div id="passwordHelp" class="form-text" v-show="passwordRules.error">{{passwordRules.message}}</div>
      </div>
      <!-- 具名插槽，v-slot 简写 #slot -->
      <template #submit>
        <span class="btn btn-primary">登陆</span>
      </template>
    </validate-form>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ValidateForm from '../components/ValidateForm.vue'
import validateInput, { RulesProp } from '../components/ValidateInput.vue'
import { useRouter } from 'vue-router'

export default defineComponent({
  name: 'App',
  components: {
    ValidateForm,
    validateInput
  },
  setup () {
    const router = useRouter()

    const inputRef = ref<any>()
    const emailVal = ref('123@qq.com')
    const emailRules: RulesProp = [
      { type: 'required', message: '邮箱地址不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱格式' }
    ]

    const passwordVal = ref('123')
    const passwordRules: RulesProp = [
      { type: 'required', message: '密码不能为空' }
    ]

    const onFormSubmit = (result: boolean) => {
      console.log(inputRef.value.validateInput())
      if (result) {
        router.push({ name: 'column', params: { id: 1 } })
      }
    }
    return {
      emailRules,
      emailVal,
      passwordVal,
      passwordRules,
      onFormSubmit,
      inputRef
    }
  }
})
</script>
