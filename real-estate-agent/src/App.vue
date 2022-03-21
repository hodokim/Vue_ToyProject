<template>

  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>{{forSale[clickedIdx].title}}</h4>
      <p>{{forSale[clickedIdx].content}}</p>
      <p>{{addComma(forSale[clickedIdx].price)}}</p>
    </div>
    <button @click="modalClose">닫기</button>
  </div>
  
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{menu}}</a>
  </div>

  <DiscountBanner/>


  
  <div v-for="(item,i) in forSale" :key="i">
    <img :src="item.image"  @click="stateChange(i); " style="width:40%" alt="">
    <h4>{{item.title}}</h4>
    <p>{{addComma(item.price)}}원</p>
  </div>
</template>

<script>
import forSaleData from './assets/forSale.js';
import DiscountBanner from './DiscountBanner.vue';

export default {
  name: 'App',
  data() {
    return {
      clickedIdx : 0,
      forSale : forSaleData,
      menus : ['메인', '매물', 'About'],
      modalOpen : false,
    }
  },
  components: {
    DiscountBanner : DiscountBanner,
  },
  methods: {
    addComma(priceVal) {
      let price = priceVal;
      return price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
    stateChange(idx) {
      this.modalOpen = true;
      this.clickedIdx = idx;
    },
    modalClose(){
      this.modalOpen = false;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

body {
  margin : 30;
}
div {
  box-sizing: border-box;
}


.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
  
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
  margin-top:10%;
} 

</style>
