<template>
    <h1>Brewary List</h1>
    City:  <input type="text" v-model="searchCity"/>
    Order by:
    <select v-model='orderBy'>
        <option value="id">Id</option>
        <option value="name">Name</option>
    </select>
    <ul>
        <li v-for="brewery in breweriesSorted" :key="brewery.id">
            {{ brewery.id }} || {{ brewery.city }} || {{ brewery.name }}
        </li>
    </ul>
</template>
<script>
import {ref, computed, watchEffect} from 'vue';
import { useApi } from './use/useApi.js';
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
                const {data, api_status, initFetch} = useApi(`${API_URL}?by_city=${searchCity.value}`);
                console.log(data.value)
                breweries = data.value
            }//if searchCity
        });//watch
        return {breweriesSorted, searchCity, orderBy}
    }//setup
};//default
</script>