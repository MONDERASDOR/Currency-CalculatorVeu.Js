<template>
  <div class="flex justify-center items-center h-screen bg-gradient-to-br from-blue-400 to-purple-600">
    <div class="bg-white shadow-2xl rounded-xl p-8 max-w-sm w-full">
      <h1 class="text-3xl font-bold text-center mb-6 text-gray-700">Currency Converter</h1>

      <div class="mb-4 relative">
        <input 
          v-model="amount" 
          type="number" 
          placeholder="Enter amount" 
          class="w-full p-3 pl-10 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-400 focus:border-transparent"
        />
        <span class="absolute left-3 top-3 text-gray-500">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6 3v-7a4 4 0 00-3-3.87M5 10v10m0 0v-2a2 2 0 012-2h3a2 2 0 012 2v2m0 0v-4m0 0V5a2 2 0 00-2-2H7a2 2 0 00-2 2v9" />
          </svg>
        </span>
      </div>

      <div class="mb-4 relative">
        <select 
          v-model="currency" 
          class="w-full p-3 pl-10 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-400 focus:border-transparent"
        >
          <option value="USD">USD - US Dollar</option>
          <option value="EUR">EUR - Euro</option>
        </select>
        <span class="absolute left-3 top-3 text-gray-500">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h3M12 3h2a2 2 0 012 2v3h-3a2 2 0 00-2 2v2H3V7a4 4 0 014-4h5V2H9a4 4 0 00-4 4v6H3V8a4 4 0 014-4h4a4 4 0 014 4v1h4V6h-2a4 4 0 00-4-4h-2a2 2 0 00-2 2h-2V6H3v2H2a2 2 0 00-2 2v3a4 4 0 004 4h5v-3H5v-4" />
          </svg>
        </span>
      </div>

      <button 
        @click="convert" 
        class="w-full bg-purple-500 text-white p-3 rounded-lg font-semibold hover:bg-purple-600 transition-colors duration-300 flex items-center justify-center"
      >
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 17v2a2 2 0 002 2h2a2 2 0 002-2v-2m-7-2V9m7-2V5a2 2 0 00-2-2H9a2 2 0 00-2 2v2a2 2 0 01-2 2H3v6h3m7-2a2 2 0 00-2-2H7" />
        </svg>
        Convert
      </button>

      <p v-if="result" class="text-center text-lg font-semibold mt-6 text-gray-800">
        Converted Amount: {{ result }}
      </p>
    </div>
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
      this.result = (this.amount * rates[this.currency]).toFixed(2);
    },
  },
};
</script>

<style scoped>
</style>
