<template>
    <h1>Brewary List (lodash demo)</h1>
    City:  <input type="text" v-model="searchCity"/>
    Order by:
    <select v-model='orderBy'>
        <option value="id">Id</option>
        <option value="name">Name</option>
    </select>
    <table>
        <thead>
            <tr>
                <td>ID</td>
                <td>Name</td>
                <td>City</td>
                <td>state</td>
                <td>Lat</td>
                <td>Long</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="brewery in breweriesSorted" :key="brewery.id" >
                <td>{{ brewery.id }} </td>
                <td><a :href="brewery.website_url">{{ brewery.name }} </a></td>
                <td>{{ brewery.city }}</td>
                <td>{{ brewery.state }}</td>
                <td>{{ brewery.latitude }}</td>
                <td>{{ brewery.longitude }}</td>
                
            </tr>
        </tbody>
    </table> 
    <!-- <ul>
        <li v-for="brewery in breweriesSorted" :key="brewery.id">
            {{ brewery.id }} || {{ brewery.city }} || {{ brewery.name }}
        </li>
    </ul> -->
</template>
<script>
import {ref, computed, watchEffect} from 'vue';
import * as _ from 'lodash';

const API_URL = 'https://api.openbrewerydb.org/breweries';

export default {
    setup(){
        const orderBy = ref('name');
        const breweriesSorted=computed(()=>
            _.sortBy(breweries.value, orderBy.value)
        );//computed

        const searchCity = ref('');
        let breweries =ref([]);

        watchEffect( ()=>{
            if(searchCity.value != ''){
                fetch(`${API_URL}?by_city=${searchCity.value}`)
                    .then(response =>{return response.json()})
                    .then(data =>{breweries.value = data});//fetch
            }//if searchCity
        });//watch
        return {breweriesSorted, searchCity, orderBy}
    }//setup
};//default
</script>