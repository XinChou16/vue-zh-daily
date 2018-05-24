<template>
  <div>
    <ul>
     <li v-for="story in storiesFilter"
      v-bind:key="story.id"
     >
        <div class="box">
          <div class="box-img">
            <img :src="story.thumbnail"  alt="img">
          </div>
          
          <div class="box-txt">
            <p>{{story.name}}</p>
            <p>{{story.description}}</p>
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
      return this.stories.slice(1,2)
    }
  },
  created() {
    axios.get('/api/4/themes')
    .then( res => {
      this.stories = res.data.others;
      console.log(this.storiesFilter);
    })
  }  
}
</script>

<style>

ul,li {
  list-style:none;
}

.box {
  /* border:1px solid #eee; */
  position: relative;
  border-radius: 5px;
  background-color: #fff;
  height: 350px;
  width: 500px;
  margin-bottom: 5px;
  line-height: 1.3;
}
 h1 {
  font-size:18px;
  margin-top: 5px;
}
.box-txt {
  position: absolute;
  bottom: 5px;
  left: 20px;
  text-align: left;
}
.box-img {
  width: 500px;
  height: 100%;
  overflow: hidden;
}
.box-img img{
  border-radius:5px;
  width: 100%;
  height: 300px;
}




</style>
