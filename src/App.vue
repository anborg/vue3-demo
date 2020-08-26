<template>
  <!-- no need to use msg.value in templates, you will have to in the setup method though -->
  <h1>{{ msg }}</h1>
  <brewery-list/>
  <h1>Meli Search Vue3 </h1>
  <meili-search />
  <!-- <brewery-search-use-api/> -->
  <!-- <h3>CountButton</h3>
  <count-button/>
  <h3>Life Cycle Hooks</h3>
  
  <lifecycle-hooks/>

  <h3>Mouse Demo</h3>
  <mouse-demo/> -->
<!-- 
  <roll-the-dice/>
  <map-device-location/>
  <map-locations-leaflet/> -->
  <!-- <map-iss/> -->
  <!-- <map-leaflet/> -->
  
</template>

<script>
import { ref } from "vue";
import BreweryList from './components/BreweryList'
//// import BrewerySearchUseApi from "./components/BrewSearchUseApi"
// import CountButton from "./components/CountButton"
// import LifecycleHooks from "./components/LifecycleHooks"
// import MouseDemo from "./components/MouseDemo"
// import RollTheDice from './components/RollTheDice'
// import MapDeviceLocation from './components/MapDeviceLocation'
// import MapLeaflet from './components/MapLeaflet'
// import MapIss from './components/MapIss'
// import MapLocationsLeaflet from './components/MapLocationsLeaflet'
import MeiliSearch from './components/MeiliSearch'
export default {
  
  setup() {
    const msg = ref("Hello, Vue 3!");
    return { msg };
  },
  components : {
    BreweryList,
    // BrewerySearchUseApi,
    // CountButton,
    // LifecycleHooks,
    // MouseDemo,
    // RollTheDice,
    // MapDeviceLocation,
    // MapLeaflet,
    // MapIss,
    // MapLocationsLeaflet
    MeiliSearch
  }
};
</script>

<style scoped>
</style>