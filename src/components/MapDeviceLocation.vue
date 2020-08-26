<template>
    <div>
        <h1>Map Device Location.  Your coordinates</h1>
        <p> latlong : { {{ coordinates.lat}}, {{ coordinates.lng}} }</p>
        <!-- <GmapMap
            :center="{lat:10, lng:10}"
            :zoom="1"
            style="width:640px,height:360px;"
        >
        </GmapMap> -->
    </div>
</template>
<script>
import { onMounted, ref} from 'vue'
import VueGeoLocation from 'vue-browser-geolocation'
// import {VueGoogleMaps} from 'vue2-google-maps'
export default {
    setup(){
        let coordinates = ref({})
        onMounted(() => {
  
            console.log("onMounted() called...");
            VueGeoLocation.getLocation({})
            .then( geoloc => {
                console.log(geoloc);
                coordinates.value = geoloc;
            })
            .catch(error => alert(error));//if user does not accept Location Req, show error
        });
        return{coordinates}
    }//setup
}
</script>