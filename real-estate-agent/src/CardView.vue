<template>
    <div>
        <img :src="forSale.image"   style="width:40%" alt="">
        <h4>{{forSale.title}}</h4>
        <p>{{addComma(forSale.price)}}원</p>
    </div>
</template>

<script>
export default {
    props : {
        forSale: Object,
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

</style>