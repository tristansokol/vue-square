<template>
<div>
  <div id="sq-ccbox">
    <!--
      You should replace the action attribute of the form with the path of
      the URL you want to POST the nonce to (for example, "/process-card")
    -->
    <form id="nonce-form" novalidate action="path/to/payment/processing/page" method="post">
      <div class="errorbox">
        <div class="error" v-for="error in errors" :key=error.message>
          {{error}}
        </div>
      </div>
      <div id="card-tainer">
        <div class="cardfields card-number" :id="id+'-sq-card-number'">o</div>
        <div class="cardfields expiration-date" :id="id+'-sq-expiration-date'">e</div>
        <div class="cardfields cvv" :id="id+'-sq-cvv'">e</div>
        <div class="cardfields postal-code" :id="id+'-sq-postal-code'">e</div>
      </div>

      <input type="hidden" id="card-nonce" name="nonce">
      <div id="sq-walletbox">
        <div v-show=!applePay class="wallet-not-enabled">Apple Pay for Web not enabled</div>
        <!-- Placeholder for Apple Pay for Web button -->
        <button v-show=applePay :id="id+'-sq-apple-pay'" class="button-apple-pay"></button>

        <div v-show=!masterpass class="wallet-not-enabled">Masterpass not enabled</div>
        <!-- Placeholder for Masterpass button -->
        <button v-show=masterpass :id="id+'-sq-masterpass'" class="button-masterpass"></button>
      </div>
    </form>
  </div>
  <button @click="requestCardNonce($event)" class='productPurchase payButton'>Pay</button>
</div>
</template>

<script>
export default {
  name: "paymentForm",
  data: function() {
    return {
      errors: [],
      masterpass: false,
      applePay: false
    };
  },
  watch: {
    showPaymentForm: function() {
      if (!this.showPaymentForm) {
        return 1;
      }
      this.paymentForm.build();
    }
  },
  props: {
    showPaymentForm: Boolean,
    id: Number
  },
  mounted: function() {
    let locationId = "75MBQ5SS3SKJK";
    let applicationId = "sq0idp-gbQhcOCpmb2X4W1588Ky7A";
    let that = this;
    this.paymentForm = new SqPaymentForm({
      autoBuild: false,
      applicationId: applicationId,
      locationId: locationId,
      inputClass: "sq-input",
      // Initialize the payment form elements

      // Customize the CSS for SqPaymentForm iframe elements
      inputStyles: [
        {
          fontSize: ".9em"
        }
      ],

      // Initialize Apple Pay placeholder ID
      applePay: {
        elementId: that.id + "-sq-apple-pay"
      },

      // Initialize Masterpass placeholder ID
      masterpass: {
        elementId: that.id + "-sq-masterpass"
      },

      // Initialize the credit card placeholders
      cardNumber: {
        elementId: that.id + "-sq-card-number",
        placeholder: "Card number"
      },
      cvv: {
        elementId: that.id + "-sq-cvv",
        placeholder: "CVV"
      },
      expirationDate: {
        elementId: that.id + "-sq-expiration-date",
        placeholder: "MM / YY"
      },
      postalCode: {
        elementId: that.id + "-sq-postal-code",
        placeholder: "Zip Code"
      },

      // SqPaymentForm callback functions
      callbacks: {
        /*
           * callback function: methodsSupported
           * Triggered when: the page is loaded.
           */
        methodsSupported: function(methods) {
          // Only show the button if Apple Pay for Web is enabled
          // Otherwise, display the wallet not enabled message.
          that.applePay = methods.applePay;
          that.masterpass = methods.masterpass;
        },

        /*
           * Digital Wallet related functions
           */
        createPaymentRequest: function() {
          var paymentRequestJson;
          /* ADD CODE TO SET/CREATE paymentRequestJson */
          return paymentRequestJson;
        },
        validateShippingContact: function(contact) {
          var validationErrorObj;
          /* ADD CODE TO SET validationErrorObj IF ERRORS ARE FOUND */
          return validationErrorObj;
        },

        /*
           * callback function: cardNonceResponseReceived
           * Triggered when: SqPaymentForm completes a card nonce request
           */
        cardNonceResponseReceived: function(errors, nonce, cardData) {
          if (errors) {
            errors.forEach(function(error) {
              that.errors.push(error.message);
            });
            return;
          }
          // Assign the nonce value to the hidden form field
          document.getElementById("card-nonce").value = nonce;

          // POST the nonce form to the payment processing page
          document.getElementById("nonce-form").submit();
        },
        /*
           * callback function: paymentFormLoaded
           * Triggered when: SqPaymentForm is fully loaded
           */
        paymentFormLoaded: function() {
          console.log("paymentFormLoaded");
          /* HANDLE AS DESIRED */
        }
      }
    });
  },
  methods: {
    requestCardNonce: function(event) {
      // Don't submit the form until SqPaymentForm returns with a nonce
      event.preventDefault();

      // Request a nonce from the SqPaymentForm object
      this.paymentForm.requestCardNonce();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
.sq-input {
  border: 1px solid rgb(223, 223, 223);
  outline-offset: -2px;
  margin-bottom: 5px;
  display: inline-block;
  border: none;
  color: #32325d;
  line-height: 18px;
  font-family: "Helvetica Neue", Helvetica, sans-serif;
  font-size: 16px;
  height: 18px;
  -webkit-font-smoothing: antialiased;
}

.sq-input ::placeholder {
  color: #aab7c4;
  opacity: 0.5;
}

/* Define how SqPaymentForm iframes should look when they have focus */

/* Define how SqPaymentForm iframes should look when they contain invalid values */

.sq-input--error {
  outline: 3px auto rgb(255, 97, 97);
}

.errorbox {
  line-height: 14px;
  text-align: left;
}

.error {
  font-size: 10px;
  color: rgb(164, 0, 30);
  width: 45%;
  display: inline-block;

  margin-top: -10px;
  font-weight: 400;
}

/* Customize the "Pay with Credit Card" button */

.button-credit-card {
  min-width: 200px;
  min-height: 20px;
  padding: 0;
  margin: 5px;
  line-height: 20px;
  box-shadow: 2px 2px 1px rgb(200, 200, 200);
  background: rgb(255, 255, 255);
  border-radius: 5px;
  border: 1px solid rgb(200, 200, 200);
  font-weight: bold;
  cursor: pointer;
}

.card-number {
  width: 100%;
}

.modal .payButton {
  margin-left: 0px;
  position: absolute;
  bottom: 0px;
  width: 400px;
}

/* Customize the "{{Wallet}} not enabled" message */

.wallet-not-enabled {
  min-width: 200px;
  min-height: 40px;
  max-height: 64px;
  padding: 0;
  margin: 10px;
  line-height: 40px;
  background: #eee;
  border-radius: 5px;
  font-weight: lighter;
  font-style: italic;
  font-family: inherit;
  display: block;
}

/* Customize the Apple Pay on the Web button */

.button-apple-pay {
  min-width: 200px;
  min-height: 40px;
  max-height: 64px;
  padding: 0;
  margin: 10px;
  background-image: -webkit-named-image(apple-pay-logo-white);
  background-color: black;
  background-size: 100% 60%;
  background-repeat: no-repeat;
  background-position: 50% 50%;
  border-radius: 5px;
  cursor: pointer;
  display: none;
}

/* Customize the Masterpass button */

.button-masterpass {
  min-width: 200px;
  min-height: 40px;
  max-height: 40px;
  padding: 0;
  margin: 10px;
  background-image: url(https://static.masterpass.com/dyn/img/btn/global/mp_chk_btn_147x034px.svg);
  background-color: black;
  background-size: 100% 100%;
  background-repeat: no-repeat;
  background-position: 50% 50%;
  border-radius: 5px;
  border-color: rgb(255, 255, 255);
  cursor: pointer;
}

#sq-walletbox {
  text-align: center;
  vertical-align: top;
  font-weight: bold;
}

#sq-ccbox {
  margin: 5px;
  padding: 0px 10px;
  text-align: center;
  vertical-align: top;
  font-weight: bold;
}

.expiration-date,
.cvv,
.postal-code {
  width: 30%;
  display: inline-block;
}

#card-tainer {
  text-align: left;
  margin-top: 8px;
  background-color: white;
  height: 80px;
  padding: 10px 12px;
  border-radius: 4px;
  border-top-left-radius: 4px;
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
  border-bottom-left-radius: 4px;
  border: 1px solid transparent;
  box-shadow: 0 1px 3px 0 #e6ebf1;
  -webkit-transition: box-shadow 150ms ease;
  transition: box-shadow 150ms ease;
  box-sizing: border-box;
}
</style>
