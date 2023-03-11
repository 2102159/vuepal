<template>
  <div class="listproduct">
    <div v-if="!paid" id="paypal-button-container"></div>
    <div v-else id="confirmation">Order complete!</div>
  </div>
</template>

<script>
import { loadScript } from "@paypal/paypal-js";
export default {
  data() {
    return {
      paid: false,
    };
  },
  beforeCreate: function () {
    loadScript({ "client-id": CLIENT_ID }).then((paypal) => {
      paypal
        .Buttons({
          createOrder: this.createOrder,
          onApprove: this.onApprove,
        })
        .render("#paypal-button-container");
    });
  },
  props: {
    cartTotal: {
      type: Number,
      default: 0.01,
    },
  },
  methods: {
    createOrder: function (data, actions) {
      console.log("Creating order...");
      return actions.order.create({
        purchase_units: [
          {
            amount: {
              value: this.cartTotal,
            },
          },
        ],
      });
    },
    onApprove: function (data, action) {
      console.log("Orden approved...");
      return action.order.capture().then(() => {
        this.paid = true;
        console.log("Order complete!");
      });
    },
  },
};
const CLIENT_ID =
  "ARPnn-6UKvEZ8a8BN9cojUYqvtdGpZg0Bo-RrCB5fp2nbvon6UBcnTwz1epTfX1JYbhrx2Pg0DSpATyF";
</script>
