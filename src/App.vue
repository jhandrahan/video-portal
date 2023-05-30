<!-- can only have one root element in the template(ex.one div) -->
<!-- when we show one component inside of another as we are doing right here with the videos component. whenever the app component renders its template with some new data that causes all the child components to be rerendered as well -->
<template>
  <div>
    <!-- v-on or @ -->
    <SearchInput @newTerm="handleNewTerm"></SearchInput>
    <!-- going to take that data property that contains videos and stuff it down into the video component. That way the videos will then receive that list of videos and once they are inside there we can figure out how to get the videos to render out on to the screen -->
    <!-- inside the child we need to bind the data from the parent component to the child componet(aka app to video)(v-bind or :)anytime the videos in the parent is updated it gets sent to the child component -->
    <Videos :videos="videos"></Videos>
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
  //any time that we have some type of variable or type of info tied to a view instance or a component, we store that information on that data property. so that means we use methods to update our data. Whenever we update our data the component automatically renders and then we can optionally make use of that computed property to somehow twist those values into something that can be displayed on the screen. we are going to take that list of videos that are returned and we are going to assign it to a property on our data object. where we are updating the data property we are atuomatically going to rerender the template
  data(){
    return {
      videos: [],
    }
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
      this.videos = data.hits;
    },
  },
};
</script>

<style>

</style>
