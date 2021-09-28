<template>
  <div id="app">
    <global-header :user="currentUser"></global-header>

    <router-view></router-view>

    <footer>
      <div>@vue3</div>
    </footer>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'

const currentUser: UserProps = {
  isLogin: true,
  name: '柠檬'
}

export default defineComponent({
  name: 'App',
  components: {
    GlobalHeader
  },
  setup () {
    return {
      currentUser
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
footer {
  width: 100%;
  background-color: #efefef;
}
</style>
