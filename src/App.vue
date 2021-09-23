<template>
<div>
<global-header :user="currentUser"></global-header>
<div class="container">
    <column-list :list="list"></column-list>
  </div>
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'

const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1专栏',
    description: '这是test1专栏描述',
    avatar: 'https://static.vue-js.com/6280b990-ff19-11ea-85f6-6fac77c0c9b3.png'
  }, {
    id: 2,
    title: 'test2专栏',
    description: '这是test2专栏描述'
  }, {
    id: 3,
    title: 'test3专栏',
    description: '这是test3专栏描述',
    avatar: 'https://static.vue-js.com/6280b990-ff19-11ea-85f6-6fac77c0c9b3.png'
  }
]

const currentUser: UserProps = {
  isLogin: false
}
export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader
  },
  setup () {
    return {
      list: testData,
      currentUser
    }
  }
})
</script>

<style>
#app {
}
</style>
