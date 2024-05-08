<template>
  <div class="conversion-widget">
    <input type="number" min="0">
    <select name="currencies" v-model="selectedCurrency">
      <template v-if="currencies">
        <option 
          v-for="(currency, key, idx) in currencies" 
          :key="idx"
          :value="key"
        >
          {{ currency }}
        </option>
      </template>
      <option v-else value="#">caricamento valute...</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    currencies: {
      type: [Object, null],
      required: true
    },
    defaultSelectedValue: {
      type: String,
      validator: function(v) {
        return v === 'USD' || v === 'EUR';
      },
      required: true
    }
  },

  data() {
    return {
      selectedCurrency: this.defaultSelectedValue,

    }
  }
}

</script>

<style>

</style>