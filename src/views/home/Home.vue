<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物车</div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar";
import {getHomeMultidata} from "../../network/home";

export default {
  name: "Home",
  components: {NavBar},
  data(){
    return {
      //定义一个初始数据为空的banner域
      banners: null
    }
  },
  created(){
    //1.请求多个数据
    //这里的res即为通过axios访问服务器所返回的值,记住这里的返回值函数写法为.then(xxx=>{})
    getHomeMultidata().then(res=>{
      console.log(res);
      //给banner域赋值，赋的值为前台访问服务器拿到的数据
      this.banners=res.data.banner.list;
      console.log(this.banners)
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