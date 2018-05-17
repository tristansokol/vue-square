<template>
<div>


  <header class="container">
    <div id="square-logo">
    </div>
  </header>
  <store />

</div>
</template>

<script>
import store from './components/store'
import 'normalize.css'

export default {
  name: 'App',
  components: {
    store
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* ==========================================================================
   Base styles: opinionated defaults
   ========================================================================== */

* {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

::-moz-selection {
    background: #b3d4fc;
    text-shadow: none;
}

::selection {
    background: #b3d4fc;
    text-shadow: none;
}

.green {
    color: #0EA50E;
}

.helperText {
    color: #8594A7;
    font-size: 12px;
    line-height: 20px;
}

a {
    -webkit-transition: all .2s ease-in-out;
       -moz-transition: all .2s ease-in-out;
        -ms-transition: all .2s ease-in-out;
            transition: all .2s ease-in-out;
}

audio,
canvas,
iframe,
img,
svg,
video {
    vertical-align: middle;
}

fieldset {
    border: 0;
    margin: 0;
    padding: 0;
}

html, body {
    color: #373F4A;
    font-size: 16px;
    line-height: 28px;
    background-color: #F7F8F9;
    font-family: SQMarket-Regular, "Helvetica Neue", Helvetica, sans-serif;
    margin: 0;
    padding: 0;
}

hr {
    display: block;
    height: 1px;
    border: 0;
    border-top: 1px solid #ccc;
    margin: 1em 0;
    padding: 0;
}

#cocoon {
    height: 100%;
    width: 100%;
    position: relative;
}

.container {
    width: 920px;
    margin: 0 auto;
}

.left { float: left; }
.right { float: right; }

.tabularFigures {
    font-variant-numeric: tabular-nums;
    -webkit-font-feature-settings: "tnum";
       -moz-font-feature-settings: "tnum";
    font-feature-settings: "tnum";
}
.tabularFigures.negative {
    margin-right: -5px;
}

body.modal-open { overflow: hidden; position: relative; }
body.modal-open #cocoon { overflow: hidden; position: relative; }

h1, h2, h3, h4, h5 {
    font-family: SQMarket-Medium, "Helvetica Neue", Helvetica, sans-serif;
    font-weight: 500;
    margin: 1em auto 0 auto;
}

h1 {
    font-size: 32px;
    line-height: 40px;
    margin-bottom: 24px;
}

h2 {
    font-size: 24px;
    line-height: 32px;
    margin-bottom: 16px;
}

h3 {
    font-size: 20px;
    line-height: 28px;
    margin-bottom: 8px;
}

h4 {
    font-size: 16px;
    line-height: 28px;
    margin-bottom: 4px;
    text-transform: uppercase;
    letter-spacing: 1px;
}

h5 {
    font-size: 16px;
    line-height: 28px;
    margin-bottom: 0px;
}

.pageTitle {
    text-align: center;
    margin-top: 0;
    margin-bottom: 40px;
}


/*
    HEADER
*/

header {
    position: relative;
    text-align: center;
    padding: 48px 0;
    height: 32px;
}

#square-logo {
    position: absolute;
    display: inline-block;
    height: 32px;
    width: 32px;
    background: url("https://cdn.glitch.com/4c9bc573-ca4c-48de-8afe-501eddad0b79%2Fsquare-logo.svg?1521834224783") center center no-repeat;
    margin: 0 auto;
    top: 50%;
    transform: translateY(-50%) translateX(-50%);
}

.back {
    height: 24px;
    border: none;
    display: inline-block;
    position: absolute;
    font-family: SQMarket-Medium, "Helvetica Neue", Helvetica, sans-serif;
    font-weight: 500;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    text-indent: 28px;
    line-height: 24px;
    color: #4A90E2;
    background: url("https://cdn.glitch.com/4c9bc573-ca4c-48de-8afe-501eddad0b79%2Ficon-back-arrow.svg?1521834225143") center left no-repeat;
    text-decoration: none;
}
.back:hover {
    color: #4281CA;
    background: url("https://cdn.glitch.com/4c9bc573-ca4c-48de-8afe-501eddad0b79%2Ficon-back-arrow-active.svg?1521834225043") center left no-repeat;
}


/*
    PRODUCTS
*/

#products {

}

.product {
    display: inline-block;
    position: relative;
    width: calc((100% - (40px * 3)) / 4);
    height: 200px;
    margin: 0 35px 40px 0;
    padding: 0;
}

.product:nth-child(4n) {
    margin-right: 0;
}

.product .imageContainer {
    position: absolute;
    height: 200px;
    width: 200px;
    border-radius: 4px;
    box-shadow: 0 0 1px 0 rgba(0,0,0,0.10), 0 2px 2px 0 rgba(0,0,0,0.10), 0 1px 2px 0 rgba(0,0,0,0.10);
    transition: all .2s ease-in-out;
    cursor: pointer;
}

.product .imageContainer:hover {
    margin-top: -2px;
    margin-bottom: 2px;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.10), 0 1px 16px 0 rgba(0,0,0,0.10), 0 2px 4px 0 rgba(0,0,0,0.10);
    filter: grayscale(100%);
}

.imageContainer .productImage {
    height: 200px;
    width: 200px;
    border-radius: 4px;
}

.imageContainer .imageOverlay {
    opacity: 0;
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background-color: rgba(0,0,0,0.5);
    text-align: center;
    border-radius: 4px;

    -webkit-transition: all .2s ease-in-out;
       -moz-transition: all .2s ease-in-out;
        -ms-transition: all .2s ease-in-out;
            transition: all .2s ease-in-out;
}

.product .imageContainer:hover .imageOverlay {
    opacity: 1;
}

.imageContainer .imageOverlay button {
    position: relative;
    top: 50%;
    transform: translateY(-50%);
    border: 1px solid #fff;
    background-color: transparent;
    border-radius: 4px;
    padding: 8px 24px;
    font-family: SQMarket-Medium, "Helvetica Neue", Helvetica, sans-serif;
    font-weight: 500;
    line-height: 24px;
    color: #fff;
    cursor: pointer;
}
.imageContainer .imageOverlay button:focus { outline: 0; }

.modal {
    position: fixed;
    top: 51%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
    opacity: 0;
    visibility: hidden;
    height: 400px;
    width: 800px;
    margin: 0 auto;
    background-color: #fff;
    box-shadow: 0 16px 24px 2px rgba(0,0,0,0.10), 0 8px 32px 4px rgba(0,0,0,0.10), 0 8px 8px 0 rgba(0,0,0,0.10);
    z-index: 1000;

    -webkit-transition: all .2s ease-in-out;
       -moz-transition: all .2s ease-in-out;
        -ms-transition: all .2s ease-in-out;
            transition: all .2s ease-in-out;
}

.modal.isOpen {
    opacity: 1;
    visibility: visible;
    top: 50%;

    -webkit-transition: all .2s ease-in-out;
       -moz-transition: all .2s ease-in-out;
        -ms-transition: all .2s ease-in-out;
            transition: all .2s ease-in-out;
}

.modal.noFade {
    top: 50%;
    -webkit-transition: all 0s ease-in-out, opacity .4s ease-in-out;
       -moz-transition: all 0s ease-in-out, opacity .4s ease-in-out;
        -ms-transition: all 0s ease-in-out, opacity .4s ease-in-out;
            transition: all 0s ease-in-out, opacity .4s ease-in-out;
}

.modal.isOpen.noFade {
    -webkit-transition: all 0s ease-in-out;
       -moz-transition: all 0s ease-in-out;
        -ms-transition: all 0s ease-in-out;
            transition: all 0s ease-in-out;
}

.veil {
    display: block;
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: #000;
    opacity: 0;
    visibility: hidden;
    z-index: 999;

    -webkit-transition: all .2s ease-in-out;
       -moz-transition: all .2s ease-in-out;
        -ms-transition: all .2s ease-in-out;
            transition: all .2s ease-in-out;
}
.veil.visible {
    opacity: 0.5;
    visibility: visible;
}



    .close {
        height: 24px;
        width: 24px;
        position: absolute;
        top: 16px;
        right: 16px;
        text-indent: -999px;
        white-space: nowrap;
        overflow: hidden;
        border: 0;
        background: url("https://cdn.glitch.com/4c9bc573-ca4c-48de-8afe-501eddad0b79%2Ficon-close-inactive.svg?1521834224941") center center no-repeat;
        transition: all .1s ease-in-out;
        cursor: pointer;
    }

    .close:hover { background: url("https://cdn.glitch.com/4c9bc573-ca4c-48de-8afe-501eddad0b79%2Ficon-close-active.svg?1521834225254") center center no-repeat; }
    .close:focus { outline: 0; }

    .modalImage {
        height: 400px;
        width: 400px;
        float: left;
    }

    .modal .productInfo {
        height: 400px;
        width: 400px;
        float: right;
    }

    .modal .productTitle {
        margin: 32px 32px 16px 32px;
    }

    .modal .productDescription {
        margin: 0 32px 0 32px;
    }

    .modal .productMeta {
        position: absolute;
        bottom: 0;
        width: 400px;
        margin-left: 32px;
        margin-right: 32px;
    }

    .modal .productCost {
        margin: 0;
        padding: 0;
    }

    .modal .productPurchase {
        width: 100%;
        height: 64px;
        margin-left: -32px;
        margin-top: 24px;
        font-family: SQMarket-Medium, "Helvetica Neue", Helvetica, sans-serif;
        font-weight: 500;
        color: #fff;
        border: 0;
        background-color: #0EA50E;
        transition: all .1s ease-in-out;
        cursor: pointer;
    }

    .modal .productPurchase:hover { background-color: #0B8C0B; }
    .modal .productPurchase:focus { outline: 0; }




/*
    CHECKOUT
*/

.panel {
    padding: 24px 32px 32px 32px;
    margin-bottom: 24px;
    background-color: #fff;
    border-radius: 4px;
    box-shadow: 0 0 1px 0 rgba(0,0,0,0.10), 0 2px 2px 0 rgba(0,0,0,0.10), 0 1px 2px 0 rgba(0,0,0,0.10);
}

.panel .panelTitle { margin-top: 0; margin-bottom: 8px; }

#paymentDetails {
    width: calc(520px - 64px);
    padding: 24px 32px 32px 32px;
    float: left;
    margin-right: 24px;
}

#orderSummary {
    width: 376px;
    float: left;
}

#orderSummary .panel {
    width: calc(376px - 64px);
    padding: 24px 32px 32px 32px;
}

.lineItems {
    border-bottom: 1px solid #F0F1F2;
    margin-top: 24px;
    margin-bottom: 24px;
}

.lineItem {
    margin-bottom: 24px;
}

.lineItem .left { max-width: 192px; }

.lineItem img {
    display: inline-block;
    box-sizing: border-box;
    height: 32px;
    width: 32px;
    border: 1px solid #EBEBEB;
    border-radius: 4px;
    margin: -2px 8px 0 0;
}

.discounts {
    border-bottom: 1px solid #F0F1F2;
    margin-top: 16px;
    margin-bottom: 24px;
}

.discount {
    margin-bottom: 24px;
}

.orderSummation {

}

.orderTotal {
    font-size: 24px;
}






/*
    CONFIRMATION
*/

#orderConfirmation {
    width: 520px;
    margin: 0 auto;
    text-align: center;
}

#orderConfirmation .panel {
    width: calc(520px - 64px);
    padding: 32px;
    margin-bottom: 40px;
}

.orderImage {
    box-sizing: border-box;
    width: 80px;
    height: 80px;
    border-radius: 4px;
    border: 1px solid #E0E2E3;
}

.button {
    border-radius: 4px;
    background-color: #4A90E2;
    line-height: 28px;
    padding: 14px 24px;
    font-family: SQMarket-Medium, "Helvetica Neue", Helvetica, sans-serif;
    font-weight: 500;
    color: #fff;
    text-decoration: none;
}
.button:hover {
    background-color: #4281CA;
}






/* ==========================================================================
   Helper classes
   ========================================================================== */

/*
 * Hide visually and from screen readers
 */

.hidden {
    display: none !important;
}

/*
 * Hide only visually, but have it available for screen readers:
 * https://snook.ca/archives/html_and_css/hiding-content-for-accessibility
 *
 * 1. For long content, line feeds are not interpreted as spaces and small width
 *    causes content to wrap 1 word per line:
 *    https://medium.com/@jessebeach/beware-smushed-off-screen-accessible-text-5952a4c2cbfe
 */

.visuallyhidden {
    border: 0;
    clip: rect(0 0 0 0);
    -webkit-clip-path: inset(50%);
    clip-path: inset(50%);
    height: 1px;
    margin: -1px;
    overflow: hidden;
    padding: 0;
    position: absolute;
    width: 1px;
    white-space: nowrap; /* 1 */
}

/*
 * Extends the .visuallyhidden class to allow the element
 * to be focusable when navigated to via the keyboard:
 * https://www.drupal.org/node/897638
 */

.visuallyhidden.focusable:active,
.visuallyhidden.focusable:focus {
    clip: auto;
    -webkit-clip-path: none;
    clip-path: none;
    height: auto;
    margin: 0;
    overflow: visible;
    position: static;
    width: auto;
    white-space: inherit;
}

/*
 * Hide visually and from screen readers, but maintain layout
 */

.invisible {
    visibility: hidden;
}

/*
 * Clearfix: contain floats
 *
 * For modern browsers
 * 1. The space content is one way to avoid an Opera bug when the
 *    `contenteditable` attribute is included anywhere else in the document.
 *    Otherwise it causes space to appear at the top and bottom of elements
 *    that receive the `clearfix` class.
 * 2. The use of `table` rather than `block` is only necessary if using
 *    `:before` to contain the top-margins of child elements.
 */

.clearfix:before,
.clearfix:after {
    content: " "; /* 1 */
    display: table; /* 2 */
}

.clearfix:after {
    clear: both;
}

.qty {
  width: 10%;
}
</style>
