<template>
<!-- start product -->
<div :id=product.id class='product'>
  <div class='imageContainer'>
    <img class='productImage' :src=product.image_url />
    <!-- insert product image url here -->
    <div class='imageOverlay' @click="showModal=true">
      <button>View Details</button>
    </div>
  </div>
  <div class='modal clearfix' :class="{isOpen:showModal}">
    <button class='close' @click="showModal=false;checkout=false">Close</button>
    <img class='modalImage' :src=product.image_url />
    <!-- insert product image url here -->
    <div class='productInfo'>
      <h2 class='productTitle'>{{product.name}}</h2>
      <!-- insert product title here -->
      <p class='productDescription'>"{{product.description}}"</p>
      <div class='productMeta' v-show="!checkout">
        <h2 class='productCost'>
                          <span class='green'>{{ product.variation.price_money.amount | price}}</span>*
                    </h2>

        <!-- insert product cost here -->
        <span class='helperText'>*We're not actually going to charge you.</span>
        <input name='itemVarID' type='hidden' :value=product.id style='display: none' />
        <input name='price' type='hidden' :value=product.variation.price_money.amount style='display: none' />
        <input name='name' type='hidden' :value=product.name style='display: none' />
        <button type='submit' class='productPurchase' @click="checkout = true">Buy This</button>



      </div>
      <paymentForm v-show="checkout" v-bind:id=product.id v-bind:showPaymentForm=checkout />
    </div>
  </div>
</div>
<!-- end product -->
</template>

<script>
import paymentForm from './paymentForm.vue'
export default {
  name: 'product',
  components: {
    paymentForm
  },
  data() {
    return {
      showModal: false,
      checkout: false
        }
  },
  watch: {
    showModal: function() {
      this.$emit('showModal', this.showModal)
    }
  },
  filters: {
  price: function (value) {
    if (!value) return ''
    value = value.toString()
    return '$'+value;
  }
},
  props: {
    product: {
      type: Object,
      default: function() {
        return {
          id: 1,
          image_url: '',
          name: 'ouaoeu',
          description: 'ouou',
          variation: {
            price_money: {
              amount: 23
            }
          }
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
