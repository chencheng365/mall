<template>
  <div>
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <h2>首页</h2>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import {getHomeMultidata} from 'network/home';

export default {
  name: "Home",
  components: {
    NavBar
  },
  data() {
    return{
      bannerData: null
    }
  },
  created() {
    getHomeMultidata().then((res) => {
      console.log(res);
      this.bannerData = res.data.banner
    }).catch((err) => {

    });
  }
};
</script>

<style scope>
.home-nav {
  color: #fff;
  background-color: var(--color-tint);
}
</style>
