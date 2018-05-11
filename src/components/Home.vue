<template>
 <div>
   <h1>今日最热</h1>
   <ul>
     <li v-for="story in storiesFilter"
        v-bind:key="story.id">
        <div class="box">
          <div class="box-txt">
            <p>{{story.title}}</p>
          </div>
          <div class="box-img">
            <img :src="story.images[0]" alt="img">
          </div>
        </div>
     </li>
   </ul>
   <img src="https://pic3.zhimg.com/v2-f3235f49a96437d5b2ea8f3ce63bd5fa.jpg" alt="">
   <!-- <ul>
     <li>
      <div class="box">
        <div class="box-txt">
          <p>{{title}}</p>
        </div>
        <div class="box-img">
          <img :src="imgUrl" alt="img">
        </div>
      </div>
     </li>
   </ul> -->
 </div>
</template>

<script>
import axios from "axios"

const API_PROXY = 'https://bird.ioliu.cn/v1/?url='
const topUrl = 'https://news-at.zhihu.com/api/4/news/latest';

export default {
  data() {
    return {
      stories: [],
      imgUrl: 'https://pic1.zhimg.com/v2-93e6fa5810552cefe8dac2fe8c173ce8.jpg',
      title: '如果你一定要吃胡萝卜，炒、煮、生啃里，我建议111111……',
    }
  },
  computed: {
    storiesFilter() {
      return this.stories.slice(0,3)
    }
  },
  created() {
    // axios.get(API_PROXY+this.topUrl)
    // .then( res => {
    //   console.log(res.data);
    // })
    // axios.get('/src/data.json')
    axios.get('/api/4/news/latest')
    .then( res => {
      // console.log(res.data);
      this.stories = res.data.stories;
    })
  }  
}
</script>

<style scoped>
.stories {
  text-align: left;
}

.box {
  border:1px solid #eee;
  border-radius: 5px;
  background-color: #fff;
  display: flex;
  height: 80px;
  width: 500px;
  padding: 5px;
  margin-bottom: 5px;
  line-height: 1.3;
}
 h1 {
  font-size:18px;
  margin-top: 5px;
}
.box-txt {
  width: 80%;
  padding: 10px;
  padding-right: 0;
  word-break: break-all;
  text-align: left;
  vertical-align: middle;
}
.box-img {
  width: 80px;
  height: 80px;
}
.box-img img{
  width: 100%;
  height: 100%;
}









</style>
