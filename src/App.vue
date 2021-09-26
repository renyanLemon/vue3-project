<template>
  <div id="app">
    <global-header :user="currentUser"></global-header>
    <form class="formLogin">
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">邮箱</label>
        <validata-input :rules="emailRules" v-model="emailVal"></validata-input>
        {{emailVal}}
        <div id="emailHelp" class="form-text" v-show="emailRules.error">{{emailRules.message}}</div>
      </div>
    </form>
    <div class="container">
      <column-list :list="list"></column-list>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
import validataInput, { RulesProp } from './components/ValidateInput.vue'

const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1',
    description: '这是test1专栏描述',
    avatar: 'https://static.vue-js.com/6280b990-ff19-11ea-85f6-6fac77c0c9b3.png'
  }, {
    id: 2,
    title: 'test2',
    description: '这是test2专栏描述'
  }, {
    id: 3,
    title: 'test3',
    description: '这是test3专栏描述',
    avatar: 'https://static.vue-js.com/6280b990-ff19-11ea-85f6-6fac77c0c9b3.png'
  }, {
    id: 4,
    title: 'test4',
    description: '这是test4专栏描述',
    avatar: 'https://static.vue-js.com/6280b990-ff19-11ea-85f6-6fac77c0c9b3.png'
  }, {
    id: 5,
    title: 'test5',
    description: '这是test5专栏描述',
    avatar: 'https://static.vue-js.com/6280b990-ff19-11ea-85f6-6fac77c0c9b3.png'
  }
]

const currentUser: UserProps = {
  isLogin: true,
  name: '柠檬'
}

export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader,
    validataInput
  },
  setup () {
    const emailVal = ref('ffff')
    console.log(333, emailVal)
    const emailRules: RulesProp = [
      { type: 'required', message: '邮箱地址不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱格式' }
    ]
    return {
      list: testData,
      currentUser,
      emailRules,
      emailVal
    }
  }
})
</script>

<style>
#app {
}
.formLogin {
  width: 300px;
}
</style>
