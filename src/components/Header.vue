<template>
  <header :style="{backgroundColor: color?color:defaultColor}">
    {{title}}
  </header>
</template>

<script lang="ts">
import { reactive, defineComponent } from '@vue/composition-api'

interface Props {
  title: string;
  color: string;
}
export default defineComponent({
  props: {
    title: String,
    color: String
  },
  setup () {
    const state = reactive({
      defaultColor: 'red'
    })
    return {
      ...state
    }
  }
})
</script>

<style scoped>
header {
  height: 50px;
  width: 100%;
  line-height: 50px;
  text-align: center;
  color: white;
}
</style>>
