<template>
  <div class="main">
    <global-header :user="currentUser"></global-header>

    <div class="content">
      <router-view></router-view>
    </div>

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
html {
  height: 100%;
}
body {
  height: 100%;
}
#app {
  height: 100%;
}
.main {
  display: flex;
  flex-direction: column;
  height: 100%;
}
.content {
  flex: 1;
}
footer {
  width: 100%;
  height: 50px;
  line-height: 50px;
  text-align: center;
  background-color: #fafafa;
}
</style>
