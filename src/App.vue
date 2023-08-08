<template>
  <div class="container">
    <GlobalHeader :user="user" />
    <ColumnList :list="list" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
const testUser: UserProps = {
  isLogin: true,
  name: 'wang'
}
const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是test1专栏'
  },
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是test1专栏',
    avatar: 'https://cdn2.thecatapi.com/images/BjIppqbNI.jpg'
  },
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是test1专栏',
    avatar: 'https://cdn2.thecatapi.com/images/BjIppqbNI.jpg'
  },
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是test1专栏',
    avatar: 'https://cdn2.thecatapi.com/images/BjIppqbNI.jpg'
  }
]
export default defineComponent({
  name: 'App',
  components: { ColumnList, GlobalHeader },

  setup() {
    return {
      list: testData,
      user: testUser
    }
  }
})
</script>

<style></style>
