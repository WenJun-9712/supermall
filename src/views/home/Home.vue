<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物车</div>
    </nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends"/>
  </div>

</template>

<script>
import NavBar from 'components/common/navbar/NavBar';
import HomeSwiper from './childComps/HomeSwiper';
import RecommendView from './childComps/RecommendView'
import {getHomeMultidata} from "network/home";


export default {
  name: 'home',
  components:{
    NavBar,
    HomeSwiper,
    RecommendView
  },
  data(){
    return{
      // result:null
      banners:[],
      recommends:[]
    }
  },
  //生命周期函数
  created () {
    //请求首页多个数据
    getHomeMultidata().then(res=>{
      // this.result=res;
      this.banners=res.data.banner.list;
      this.recommends=res.data.recommend.list;
    })
  }
}
</script>

<style scoped>
  .home-nav{
    background-color: var(--color-tint);
    color: #ffffff;
  }
</style>
