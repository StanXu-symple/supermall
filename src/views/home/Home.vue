<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <home-recommend-view :recommends="recommends"></home-recommend-view>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar";
import HomeSwiper from "@/views/home/childComps/HomeSwiper";
import HomeRecommendView from "@/views/home/childComps/HomeRecommendView";

import {getHomeMultidata} from "../../network/home";

export default {
  name: "Home",
  components: {
    HomeRecommendView,
    NavBar,
    HomeSwiper
  },
  data(){
    return {
      //定义一个初始数据为空的banner域
      banners: [],
      recommends: []
    }
  },
  created(){
    //1.请求多个数据
    //这里的res即为通过axios访问服务器所返回的值,记住这里的返回值函数写法为.then(xxx=>{})
    getHomeMultidata().then(res=>{
      console.log(res);
      //给banner域赋值，赋的值为前台访问服务器拿到的数据
      this.banners=res.data.banner.list;
      this.recommends=res.data.recommend.list;
      console.log(this.banners);
    })
  }
}
</script>

<style scoped>
.home-nav {
  background-color: var(--color-tint);
  color: white;
}
</style>