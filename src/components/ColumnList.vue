<template>
    <div class="row">
        <div v-for="column in columnList" :key="column.id" class="col-4">
          <div class="card">
            <img :src="column.avatar" alt="头像">
            <div class="card-body">
              <h5>{{column.title}}</h5>
              <p>{{column.description}}</p>
              <a href="#">进入专栏</a>
            </div>
          </div>
        </div>
    </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from 'vue'

export interface ColumnProps {
    id: number;
    title: string;
    avatar?: string;
    description: string;
}

export default defineComponent({
  name: 'ColumnList',
  props: {
    list: {
      type: Array as PropType<ColumnProps[]>,
      required: true
    }
  },
  setup (props) {
    const columnList = computed(() => {
      return props.list.map(column => {
        if (!column.avatar) {
          column.avatar = require('@/assets/vue3.png')
        }
        return column
      })
    })
    return {
      columnList
    }
  }
})

</script>

<style scoped>
img {
  height: 300px;
}
</style>
