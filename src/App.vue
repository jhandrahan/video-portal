<!-- can only have one root element in the template(ex.one div) -->
<template>
  <div>
    <SearchInput @newTerm="handleNewTerm"></SearchInput>
    <Videos></Videos>
  </div>
</template>

<script>
import SearchInput from './components/SearchInput.vue';
const API_KEY = "36888316-a89b50a81da9f87b4a6240c6d";
import Videos from './components/Videos.vue';
export default {
  
  name: "App",
  components:{
    SearchInput,
    Videos,
  },
  methods:{
  //any time that we make a request over the network, it takes some amount of time to complete that request,
  //the fetch method returns a promise which allows us to get a notification when the request is complete,
  //so we can handle that promise just by using async await syntax
  //the word async before a function means one simple thing a function always returns a promise
  //other values are wrapped in a resolved promise automatically
  //async basically ensures taht the function returns a promise and it wraps non promises in it
  //await only works inside aysnc functions. async makes JS wait until that promise settles and returns its result
  //await literally suspends the function execution until the problem is settled and then resumes with the promise result
    handleNewTerm: async function(searchInput){
      const response = await fetch('https://pixabay.com/api/videos/?' + 
      new URLSearchParams({
        key: API_KEY,
        q: searchInput
      }))
      const data = response.json()
      console.log(data)
    },
  },
};
</script>

<style>

</style>
