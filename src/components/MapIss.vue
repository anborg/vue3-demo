
<template lang="html">

  <div class="row">
    <div>
      <h2>Map Iss</h2>
    </div>
    <div id="map">

    </div>
  </div>
</template>


<script>
    import L from 'leaflet'

    export default {
        
        setup(){
            // Making a map and tiles
          // Setting a higher initial zoom to make effect more obvious
          let mymap = L.map('issMap').setView([0, 0], 6);
          mounted(){
            mymap = L.map('issMap').setView([0, 0], 6);
          }
          const attribution = '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors';
        
          const tileUrl = 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png';
          const tiles = L.tileLayer(tileUrl, { attribution });
          tiles.addTo(mymap);

          // Making a marker with a custom icon
          const issIcon = L.icon({
            iconUrl: 'iss200.png',
            iconSize: [50, 32],
            iconAnchor: [25, 16]
          });
          let marker = L.marker([0, 0], { icon: issIcon }).addTo(mymap);

          const api_url = 'https://api.wheretheiss.at/v1/satellites/25544';

          let firstTime = true;
            let lat = 0;


            function getISS() {
            const response =  fetch(api_url); //await
            const data =  response.json(); //await
            const { latitude, longitude } = data;

            // Always set the view to current lat lon and zoom!
            mymap.setView([latitude, longitude], mymap.getZoom());
            marker.setLatLng([latitude, longitude]);

            lat= latitude.toFixed(2);
            document.getElementById('lon').textContent = longitude.toFixed(2);
          }

            setInterval(() => {
            getISS;
            }, 1000);

          return(lat, mymap,attribution,tileUrl, tiles,issIcon,marker,api_url,firstTime,getISS)

        }
    }

</script>