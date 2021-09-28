<template>
  <div class="container">
      <column-list :list="list"></column-list>
    </div>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from '../components/ColumnList.vue'

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
  }
]

export default defineComponent({
  name: 'App',
  components: {
    ColumnList
  },
  setup () {
    return {
      list: testData
    }
  }
})
</script>
