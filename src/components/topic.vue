<template>
  <div>
   <ul>
     <li v-for="story in storiesFilter"
        v-bind:key="story.id">
        <div class="box">
          <div class="box-txt">
            <p>{{story.name}}</p>
            <p>{{story.description}}</p>
          </div>
          <div class="box-img">
            <img :src="story.thumbnail" alt="img">
          </div>
        </div>
     </li>
   </ul>
  </div>
</template>

<script>
import axios from "axios"

export default {
  data() {
    return {
      stories: []
    }
  },
  computed: {
    storiesFilter() {
      return this.stories.slice(0,3)
    }
  },
  created() {
    axios.get('/api/4/themes')
    .then( res => {
      this.stories = res.data.others;
    })
  }  
}
</script>

<style>

</style>
