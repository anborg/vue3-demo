<template>
  <!-- no need to use msg.value in templates, you will have to in the setup method though -->
  <h1>{{ msg }}</h1>
  <brewery-list/>
  <!-- <brewery-search-use-api/> -->
  <h3>CountButton</h3>
  <count-button/>
  <h3>Life Cycle Hooks</h3>
  
  <lifecycle-hooks/>

  <h3>Mouse Demo</h3>
  <mouse-demo/>

</template>

<script>
import { ref } from "vue";
import BreweryList from './components/BreweryList'
// import BrewerySearchUseApi from "./components/BrewSearchUseApi"
import CountButton from "./components/CountButton"
import LifecycleHooks from "./components/LifecycleHooks"
import MouseDemo from "./components/MouseDemo"
export default {
  
  setup() {
    const msg = ref("Hello, Vue 3!");
    return { msg };
  },
  components : {
    BreweryList,
    // BrewerySearchUseApi,
    CountButton,
    LifecycleHooks,
    MouseDemo
  }
};
</script>

<style scoped>
</style>