<template>
    <nav class="navbar navbar-dark justify-content-between" style="padding:10px 80px;background-color: #3eaf7c;">
        <a class="navbar-brand" href="#">vue3专栏</a>
        <div v-if="!user.isLogin">
            <button type="button" class="btn btn-primary">登陆</button>
            <button type="button" class="btn btn-success">注册</button>
        </div>
        <div v-else>
            <dropdown :title="user.name">
              <dropdown-item><a href="#" class="dropdown-item">新建文章</a></dropdown-item>>
              <dropdown-item><a href="#" class="dropdown-item">编辑资料</a></dropdown-item>>
              <dropdown-item><a href="#" class="dropdown-item">退出登陆</a></dropdown-item>>
            </dropdown>
        </div>
    </nav>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import Dropdown from './Dropdown.vue'
import DropdownItem from './DropdownItem.vue'
export interface UserProps {
    isLogin: boolean;
    name?: string;
    id?: number;
}

export default defineComponent({
  name: 'GlobalHeader',
  components: {
    Dropdown,
    DropdownItem
  },
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
