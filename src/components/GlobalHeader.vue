<template>
    <nav class="navbar navbar-dark bg-dark justify-content-between" style="padding:10px 20px">
        <a class="navbar-brand" href="#">vue3专栏</a>
        <div v-if="!user.isLogin">
            <button type="button" class="btn btn-primary">登陆</button>
            <button type="button" class="btn btn-success">注册</button>
        </div>
        <div v-else>{{user.name}}</div>
    </nav>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

export interface UserProps {
    isLogin: boolean;
    name?: string;
    id?: number;
}

export default defineComponent({
  name: 'GlobalHeader',
  props: {
    user: {
      type: Object as PropType<UserProps>,
      require: true
    }
  }
})

</script>

<style scoped>

</style>
