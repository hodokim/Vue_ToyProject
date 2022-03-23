<template>

  
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{menu}}</a>
  </div>

  <DiscountBanner></DiscountBanner>

  <transition name="fade">
    <DetailModal @modalClose="modalClose()" 
    :forSale="forSale" :clickedIdx="clickedIdx" :modalOpen="modalOpen"/>
  </transition>

  
  <CardView @modalOpen="stateChange($event)" 
  v-for="item in forSale" :key="item" :forSale="forSale[item.id]"></CardView>




  
  

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

.start {
  opacity: 0;
  transition: all 0.7s;
}

.end {
  opacity: 1;
  transition: all 0.7s;
}

/* 작명-enter-from 
  from : 애니메이션 동작 전 상태
  active : 애니메이션 동작 중 상태, 대부분 transition.. 같은
  to : 애니메이션 동작 후 상태
*/
.fade-enter-from{
  /* transform: translateY(-1000px); */
  opacity: 0;
}
.fade-enter-active{
  transition: all 0.5s;
}
.fade-enter-to{
  opacity: 1;
}

/* 작명-leave-from */
.fade-leave-from{
  opacity: 1;
}
.fade-leave-active{
  transition: all 0.5s;
}
.fade-leave-to{
  opacity: 0;
}


body {
  margin : 30;
}
div {
  box-sizing: border-box;
}

</style>
