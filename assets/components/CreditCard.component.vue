<script setup>
import Background from '@/components/background.component.vue';
import Cards from '@/components/cards.component.vue';
</script>

<template>
  <Background/>
  <Cards :cardNumber="cardNumber" :cardName="cardName" :cardExpDateMonth="cardExpDateMonth" :cardExpYear="cardExpYear" cardCvv="cardCvv"/>

  <section class="userInput right">
      <div class="userInput__cardName display-grid">
        <label for="cardName">Cardholder Name</label>
        <input type="text" id="cardName" v-model="cardName" placeholder="Max Mustermann"/>
      </div>
      <div class="userInput__cardNumber display-grid">
        <label for="cardNumber">Card Number</label>
        <input type="number" id="cardNumber" v-model="cardNumber" placeholder="4513 2568 5876 0869" maxlength="18" @keyup="cardNumberInput"/>
      </div>
  </section>

</template>

<script>
export default {
  name: "CreditCard.component.vue",
  data() {
    return {
      cardNumber: "",
      cardName: "",
      cardExpMonth: "",
      cardExpYear: "",
      cardCvv: "",
    };
  },
  methods: {
    cardNumberInput() {
      const input = document.getElementById("cardNumber");
      let content = input.value.split(" ").join("");
      if (content.length > 0) {
        content = content.match(new RegExp('.{1,4}', 'g')).join(" ");
      }
      input.value = content;
    }
  }
}
</script>

<style scoped>
@import "@/styles/CreditCard/CreditCard.css";
</style>