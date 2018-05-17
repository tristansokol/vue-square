<template>
<div id="products" class="container clearfix">

  <product v-for="product in products" v-bind:key="product.id" v-bind:product="product" v-on:showModal="showVeil = $event"/>
  <div class="veil " :class="{visible:showVeil}"></div>
</div>
</template>

<script>
import product from './product.vue'
export default {
  name: 'store',
  components: {
    product
  },
  data() {
    return {
      showVeil:false,
      products: [{
        id: 1,
        image_url: 'https://square-production.s3.amazonaws.com/files/e7cdf61251e5618d64577b4b19033036dbcf1018/original.jpeg',
        name: 'Back to Square 1 Sticker',
        description: 'If only 88 was a perfect Square...',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 2,
        image_url: 'https://square-production.s3.amazonaws.com/files/93dd6a6f763d0866c6bccded2ca279ebf8f36794/original.jpeg',
        name: 'Enter Squandman Sticker',
        description: 'Our cover band is a mix between Mesquallica and Def Squeppard',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 3,
        image_url: 'https://square-production.s3.amazonaws.com/files/25478c801bde5ba582abaebb3eede2e80830d173/original.jpeg',
        name: 'Gamer Squared Sticker',
        description: '8-bit gamers unite.',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 4,
        image_url: 'https://square-production.s3.amazonaws.com/files/283e86efe59f59709c5f5ea1ace43a522adb394c/original.jpeg',
        name: 'Squarely Eighties Sticker',
        description: 'What could be more 80s than neon, jewels and blocks?',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 5,
        image_url: 'https://square-production.s3.amazonaws.com/files/eee2bd7a500e9ad794b2fbc839e33020dba8997f/original.png',
        name: 'Squid Hat',
        description: 'For all those sport games. Keep the sun out of your eyes with this Square Cap. Orange of course.',
        variation: {
          price_money: {
            amount: 23
          }
        }
      },{
        id: 6,
        image_url: 'https://square-production.s3.amazonaws.com/files/59f662d8441ca3846bb9d4c456e1e2c72b398c0d/original.jpeg',
        name: 'Squocks',
        description: 'A pair of unisex socks. One size may not fit all, but your toes will be comfy cozy.',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 7,
        image_url: 'https://square-production.s3.amazonaws.com/files/f59d130ae262736c909ae5a283396bbb2ec17446/original.png',
        name: 'PopSquocket',
        description: 'Get a Squared grip on your phone.',
        variation: {
          price_money: {
            amount: 23
          }
        }
      },{
        id: 8,
        image_url: 'https://square-production.s3.amazonaws.com/files/fdba3aeec501169a0858067715ab9b36017059e5/original.jpeg',
        name: 'Sq80s Overdrive Sticker',
        description: 'Throw back sticker.',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 9,
        image_url: 'https://square-production.s3.amazonaws.com/files/d0a25161e4b1f4bbe90a47b2bdc21d35e60509ed/original.jpeg',
        name: 'SQLU Sticker',
        description: 'Square Likeness Utility Program.',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 10,
        image_url: 'https://square-production.s3.amazonaws.com/files/971b9a519a891d6132d73022b9643257b7cf4a69/original.png',
        name: 'Squ(h)at',
        description: 'A branded Square, off-branded Lid. Blue of course',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 11,
        image_url: 'https://square-production.s3.amazonaws.com/files/3e04784cd73e9d95f24cc3179f860b7f0c9d596e/original.png',
        name: 'Squap',
        description: 'Keep your hair out of your face while you exercise with this lovely hat. Purple of course.',
        variation: {
          price_money: {
            amount: 1
          }
        }
      },{
        id: 12,
        image_url: 'https://square-production.s3.amazonaws.com/files/9c1271ffd3cd16df7814bd7a50e2de8965b38fe0/original.jpeg',
        name: 'Squoley Moley!',
        description: 'Oh wow, a Developers Squared moleskin! Pocket sized with grid paper! Those are rare.',
        variation: {
          price_money: {
            amount: 1
          }
        }
      }]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
