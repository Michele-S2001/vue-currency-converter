<script>
import axios from 'axios';
import store from './store';
import CurrencyConversionWidget from './components/CurrencyConversionWidget.vue';

export default {
  components: {
    CurrencyConversionWidget
  },

  data() {
    return {
      currencies: null
    }
  },

  methods: {
    fetchCurrencies() {
      axios
        .get(`${store.BASE_API_URL}/currencies`)
        .then(res => {
          this.currencies = res.data;
        })
    }
  },

  mounted() {
    this.fetchCurrencies();
  }
}

</script>

<template>
  <h1>ciao</h1>
  <CurrencyConversionWidget :currencies="currencies" :defaultSelectedValue="'EUR'"/>
  <CurrencyConversionWidget :currencies="currencies" :defaultSelectedValue="'USD'"/>
</template>

<style>

</style>
