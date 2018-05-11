<template>
<div id="app">  
  <div class="wrap">
    <ul>
      <li><router-link to="/">首页</router-link></li>
      <li><router-link to="/topic">主题</router-link></li>
      <li><router-link to="/about">关于</router-link></li>
    </ul>
  </div>
  <router-view></router-view>
</div>
</template>

<script>
import Home from "./components/home";
import Topic from "./components/topic";
import About from "./components/about";
import VueRouter from "vue-router";


const router = new VueRouter({
  routes: [
    { path: "/", component: Home },
    { path: "/topic", component: Topic },
    { path: "/about", component: About }
  ]
});
export default {
  name: 'app',
  router,
  data () {
    return {
      msg: 'Welcome to Your Vue.js App1'
    }
  },
  components:{
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size:16px;
  background-color: #eee;
}
h1, h2 {
  font-weight: normal;
}

ul,
li {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}
li a:hover {
  color: #eeeeee;
}

a {
  color: #fff;
  text-decoration: none;
  margin-right: 10px;
}
.wrap {
  background-color: #42b983;
  height: 2em;
  line-height: 2em;
}
</style>
