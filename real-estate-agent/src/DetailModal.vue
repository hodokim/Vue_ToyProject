<template>
    <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>{{forSale[clickedIdx].title}}</h4>
      <p>{{forSale[clickedIdx].content}}</p>
      <p>{{addComma(forSale[clickedIdx].price)}}</p>
    </div>
    <!-- <button @click="$emit(modalOpen = false)">닫기</button> -->
  </div>
</template>

<script>
export default {
    name: 'DetailModal',
    props:{
      forSale : Object,
      clickedIdx : Number,
      modalOpen : Boolean,
    },
    methods:{
      addComma(priceVal) {
      let price = priceVal;
      return price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
    }
}
</script>

<style>
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