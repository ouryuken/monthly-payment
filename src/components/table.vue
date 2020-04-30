<template>
  <div>
    <form class="section">
      <label class="label">Horas Trabajadas</label>
      <div class="field">
        <div class="control">
          <input class="input" type="number" max="200" min="1" placeholder="Horas Trabajadas" required v-model="workedHours">
        </div>
      </div>

      <label class="label">Horas Totales</label>
      <div class="field">
        <div class="control">
          <input class="input" type="number" max="200" min="1" placeholder="Horas Totales" required v-model="totalHours">
        </div>
      </div>

      <label class="label">Monto Mensual</label>
      <div class="field has-addons">
        <div class="control">
          <span class="select">
            <select v-model="currency">
              <option v-for="currency in allCurrencies" :key="currency.code">{{currency.code}}</option>
            </select>
          </span>
        </div>
        <div class="control" style="width: 100%;">
          <input class="input is-fullwidth" type="number" min="1" max="99999" placeholder="Monthly Fee" required v-model="monthlyFee">
        </div>
      </div>
    </form>

    <div class="section">
      <table class="table is-bordered is-striped">
        <tbody>
          <tr>
            <th>Cantidad de horas trabajadas:</th>
            <td>{{workedHours}}</td>
          </tr>
          <tr>
            <th>Cantidad de horas totales:</th>
            <td>{{totalHours}}</td>
          </tr>
          <tr>
            <th>Valor del monthly fee:</th>
            <td>{{currentCurrency.symbol}}{{monthlyFee}}</td>
          </tr>
          <tr>
            <th>Total</th>
            <td>{{currentCurrency.symbol}}{{totalPay}}</td>
          </tr>
          <tr>
            <th>Currency</th>
            <td>{{currentCurrency.code}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import currencies from '../data/currencies.json';

const allCurrencies = Object.values(currencies);
let currency = 'USD';
let workedHours = 1;
let totalHours = 176;
let monthlyFee = 1;

export default {
  name: 'Table',
  props: {
  },
  data: () => ({
    workedHours,
    totalHours,
    monthlyFee,
    currency,
    allCurrencies
  }),
  computed: {
    totalPay: function() { 
      let total = this.workedHours * this.monthlyFee / this.totalHours

      return total.toFixed(2);
    },
    currentCurrency: function() {
      return this.allCurrencies.find(o => o.code === this.currency)
    }
  }
}
</script>

<style scoped>
</style>
