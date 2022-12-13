<template>
  <div class="ticker-wrap">
    <div class="ticker">
      <div class="ticker__item">Latest crypto prices</div>
      <div class="ticker__item">Bitcoin (BTC): ${{ btcPrice }}</div>
      <div class="ticker__item">Ethereum (ETH): ${{ ethPrice }}</div>
      <div class="ticker__item">Litecoin (LTC): ${{ ltcPrice }}</div>
      <div class="ticker__item">Paraswap (PSP): ${{ pspPrice }}</div>
      <div class="ticker__item">
        <!-- Make this look like an actual link -->
        <!-- underline -->
        <!-- color -->

        <a
          href="https://go.offchaininsights.com/phemex"
          target="_blank"
          rel=""
          class="underline text-blue-100"
          >Get a $180 Welcome Bonus</a
        >
        | Trade Crypto with 100x Leverage
      </div>

      <!--<div class="ticker__item">Authentic bitters seitan pug single-origin coffee whatever.</div>
  <div class="ticker__item">Letterpress chambray brunch.</div>
  <div class="ticker__item">Vice mlkshk crucifix beard chillwave meditation hoodie asymmetrical Helvetica.</div>
  <div class="ticker__item">Ugh PBR&B kale chips Echo Park.</div>
  <div class="ticker__item">Gluten-free mumblecore chambray mixtape food truck. </div>
  <div class="ticker__item">Authentic bitters seitan pug single-origin coffee whatever.</div>-->
    </div>
  </div>
  <!-- <div class="flex flex-col items-center rotating-price-ticker">
    <div class="flex flex-row justify-between w-3/4">
      <div class="px-4 py-2 bg-gray-200 rounded-lg text-center">
        Bitcoin (BTC)
      </div>
      <div class="px-4 py-2 bg-gray-300 rounded-lg text-center">
        $ {{ btcPrice }}
      </div>
    </div>
    <div class="flex flex-row justify-between w-3/4 mt-2">
      <div class="px-4 py-2 bg-gray-200 rounded-lg text-center">
        Ethereum (ETH)
      </div>
      <div class="px-4 py-2 bg-gray-300 rounded-lg text-center">
        $ {{ ethPrice }}
      </div>
    </div>
    <div class="flex flex-row justify-between w-3/4 mt-2">
      <div class="px-4 py-2 bg-gray-200 rounded-lg text-center">
        Litecoin (LTC)
      </div>
      <div class="px-4 py-2 bg-gray-300 rounded-lg text-center">
        $ {{ ltcPrice }}
      </div>
    </div>
  </div> -->
</template>

<script>
export default {
  data() {
    return {
      btcPrice: '',
      ethPrice: '',
      ltcPrice: '',
      pspPrice: '',
    }
  },

  mounted() {
    this.fetchPrices()
  },
  beforeDestroy() {
    clearInterval(this.interval)
  },

  methods: {
    fetchPrices() {
      fetch(
        'https://api.coingecko.com/api/v3/simple/price?ids=bitcoin%2Cethereum%2Clitecoin%2Cparaswap&vs_currencies=usd'
      )
        .then((response) => response.json())
        .then((data) => {
          this.btcPrice = data.bitcoin.usd
          this.ethPrice = data.ethereum.usd
          this.ltcPrice = data.litecoin.usd
          this.pspPrice = data.paraswap.usd
        })
    },
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}

@-webkit-keyframes ticker {
  0% {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    visibility: visible;
  }

  100% {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
  }
}

@keyframes ticker {
  0% {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    visibility: visible;
  }

  100% {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
  }
}

.ticker-wrap {
  position: relative;
  top: 0;
  /* max-width: 100%; */
  overflow: hidden;
  height: 3rem;
  /* background-color: gray; */
  /* make the background color a gradient */
  background: linear-gradient(90deg, #f6d365 0%, #fda085 100%);

  padding-left: 0%;
  box-sizing: content-box;
}

.ticker-wrap .ticker {
  display: inline-block;
  height: 3rem;
  line-height: 3rem;
  white-space: nowrap;
  padding-right: 0%;
  box-sizing: content-box;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
  -webkit-animation-timing-function: linear;
  animation-timing-function: linear;
  -webkit-animation-duration: 35s;
  animation-duration: 35s;
  -webkit-animation-name: ticker;
  animation-name: ticker;

  /* restart the animation once the last ticker element reaches the end */
  -webkit-animation-play-state: running;
  animation-play-state: running;

  -webkit-animation-delay: 0s;
  animation-delay: 0s;

  -webkit-animation-fill-mode: forwards;
  animation-fill-mode: forwards;

  -webkit-animation-direction: normal;
  animation-direction: normal;
}

.ticker-wrap .ticker__item {
  display: inline-block;
  padding: 0 2rem;
  font-size: 1rem;
  color: white;
  font-weight: 100;
  /* text-transform: uppercase; */
  letter-spacing: 0.1rem;
  font-family: 'Roboto', sans-serif;
}
</style>
