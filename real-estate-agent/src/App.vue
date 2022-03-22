<template>

  <DetailModal :forSale="forSale" :clickedIdx="clickedIdx" :modalOpen="modalOpen"/>
  
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{menu}}</a>
  </div>

  <DiscountBanner></DiscountBanner>

  <CardView v-for="item in forSale" :key="item" :forSale="forSale[item.id]"></CardView>


  
  

</template>

<script>
import forSaleData from './assets/forSale.js';
import DiscountBanner from './DiscountBanner.vue';
import DetailModal from './DetailModal.vue';
import CardView from './CardView.vue';

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
    DetailModal : DetailModal,
    CardView : CardView,
  },
  methods: {
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

</style>
