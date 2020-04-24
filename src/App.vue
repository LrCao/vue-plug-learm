<template>
  <div id="app">
    <Header title="Eno" color="red" />
    <Search />
    <Panel  />
    <div id="nav">
      <h2>{{ msg }}</h2>
      <p>count is {{ count }}</p>
      <p>plusOne is {{ plusOne }}</p>
      <button @click="increment">count++</button>
      <!-- <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> -->
    </div>
    <!-- <router-view/> -->
  </div>
</template>

<script lang="ts">
import { ref, computed, watch, onMounted, Ref, defineComponent } from '@vue/composition-api'

import Header from './components/Header.vue'
import Search from './components/Search.vue'
import Panel from './components/Panel.vue'

interface Props {
  name: string;
}

export default defineComponent({
  props: {
    name: {
      type: String,
      default: 'sss'
    }
  },
  components: { Header, Search, Panel },
  setup (props: Props) {
    const count: Ref<number> = ref(0)
    // computed
    const plusOne = computed(() => count.value + 1)

    const increment = () => {
      count.value++
    }

    watch(() => count.value * 2, val => {
      console.log(`count * 2 is ${val}`)
    })

    onMounted(() => {
      console.log('onMounted')
    })

    return {
      count,
      plusOne,
      increment,
      msg: `hello ${props.name}`
    }
  }
})
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
