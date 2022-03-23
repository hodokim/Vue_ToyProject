<template>
    <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>{{forSale[clickedIdx].title}}</h4>
      <p>{{forSale[clickedIdx].content}}</p>
      <input v-model="month">
      <p>{{month}}개월 선택함 : {{addComma(forSale[clickedIdx].price * month)}}</p>
      <button @click="$emit('modalClose')" >닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'DetailModal',
    data() {
      return {
        month : 1,
      }
    },
    watch : {
      // 위의 data 명과 같아야 한다.
      month(val) {
        this.month = val.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1')
        
        if(val>12 ) {
          console.log('13개월은  곤란해');
          this.month = 1;
          return;
        }
        
      }
    },
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