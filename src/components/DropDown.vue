<template>
  <div class="dropdown" ref="dropdownRef">
    <a
      href="www.baidu.com"
      class="btn btn-outline-light my-2 dropdown-toggle"
      @click.prevent="change"
    >
      {{ title }}
    </a>
    <ul :class="{ 'dropdown-menu': true, show: isOpen }">
      <slot></slot>
    </ul>
  </div>
</template>
<script lang="ts">
import { defineComponent, onMounted, onUnmounted, ref, watch } from 'vue'
import useIsClickOutside from '../hocks/useClickOutside'
export default defineComponent({
  name: 'DropDown',
  props: {
    title: {
      type: String,
      required: true
    }
  },
  setup() {
    const dropdownRef = ref<null | HTMLElement>(null)
    const isOpen = ref(false)
    function change() {
      isOpen.value = !isOpen.value
    }
    const isClickOutside = useIsClickOutside(dropdownRef)
    watch(isClickOutside, () => {
      if (isOpen.value && isClickOutside.value) {
        isOpen.value = false
      }
    })

    return { change, isOpen, dropdownRef }
  }
})
</script>
<style scoped>
.show {
  display: block;
}
</style>
