<template>
  <div>
    <h1>Currency Converter</h1>
    <input v-model="amount" placeholder="Amount" />
    <select v-model="currency">
      <option value="USD">USD</option>
      <option value="EUR">EUR</option>
    </select>
    <button @click="convert">Convert</button>
    <p v-if="result">Converted Amount: {{ result }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      amount: '',
      currency: 'USD',
      result: null,
    };
  },
  methods: {
    convert() {
      const rates = {
        USD: 1.0,
        EUR: 0.85,
      };
      this.result = this.amount * rates[this.currency];
    },
  },
};
</script>
