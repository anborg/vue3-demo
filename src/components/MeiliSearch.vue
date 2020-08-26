<template>
  <ais-instant-search :search-client="searchClient" index-name="steam-video-games">
    <ais-search-box />
    <ais-hits>
      <div >
        <h2>{{ item.name }}</h2>
      </div>
    </ais-hits>
  </ais-instant-search>
</template>

<script>
// import InstantSearch from 'vue-instantsearch';
import {instantMeiliSearch} from '@meilisearch/instant-meilisearch';

export default {
  setup() {
    return {
      searchClient: instantMeiliSearch(
        "https://demos.meilisearch.com",
        "dc3fedaf922de8937fdea01f0a7d59557f1fd31832cb8440ce94231cfdde7f25"
      ),
    };
  },
};
</script>

<style>
body {
  font-family: sans-serif;
  padding: 1em;
}
</style>