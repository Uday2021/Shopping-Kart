<template>
  <div class="home">
    <ProductDescriptionDrawer 
    :product="product"
    :active="active.product_drawer "
    v-on:close-product-drawer="closeProductDrawer"/>
    <div class="product-cards-container">
      <ProductSummaryCard 
      v-for="product in items"
      :key="product.id"
      :product="product"
      v-on:view-product="viewProduct($event)"/>
    </div>
  </div>
</template>

<script>
import ProductSummaryCard from '../components/Products/ProductSummaryCard'
import ProductDescriptionDrawer from '../components/Products/ProductDescriptionDrawer'
import items from '../data/items'
export default {
  name: 'Home',
  components: {
    ProductSummaryCard,ProductDescriptionDrawer,
  },
  data(){
    return{
      
    items:items,
    product: null,
    active:{
      product_drawer:false
    }
    }
  },
  methods:{
      viewProduct(product){
        this.product = product;
        this.active.product_drawer= true;
        console.log(this.product);
      },
      closeProductDrawer(){
        this.active.product_drawer= false;
      }
  }
}
</script>

<style lang="scss">
.product-cards-container{
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}
</style>
