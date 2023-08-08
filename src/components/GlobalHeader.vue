<template>
  <nav
    class="navbar navbar-expand-lg navbar-dark bg-primary justify-content-between p-3"
  >
    <a class="navbar-brand" href="#"> 者也专栏</a>
    <ul v-if="!user1.isLogin" class="list-inline mb-0">
      <li class="list-inline-item">
        <a href="#" class="btn btn-outline-light my-2">login</a>
      </li>
      <li class="list-inline-item">
        <a href="#" class="btn btn-outline-light my-2">register</a>
      </li>
    </ul>
    <ul v-else class="list-inline mb-0">
      <li class="list-inline-item">
        <DropDown :title="`welcome${user1.name}`">
          <DropDownItem disabled>
            <a href="#" class="dropdown-item">new essay</a>
          </DropDownItem>
          <DropDownItem>
            <a href="#" class="dropdown-item">edit documentation</a>
          </DropDownItem>
        </DropDown>
      </li>
    </ul>
  </nav>
</template>
<script lang="ts">
import { defineComponent, PropType } from 'vue'
import DropDown from './DropDown.vue'
import DropDownItem from './DropDownItem.vue'
export interface UserProps {
  isLogin: boolean
  name?: string
  id?: number
}
export default defineComponent({
  name: 'GlobalHeader',
  components: { DropDown, DropDownItem },
  props: {
    user: {
      type: Object as PropType<UserProps>,
      required: true
    }
  },
  setup(props) {
    return {
      user1: props.user
    }
  }
})
</script>
