<template>
  <div>
    <div id="cards" v-for="currency in currencies" :key="currency.name">
      <card :name="currency.name" :price_usd="currency.price_usd" :percent_change_1h="currency.percent_change_1h"></card>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "~/components/Card.vue";

export default {
  asyncData() {
    return axios
      .get("https://api.coinmarketcap.com/v1/ticker/?limit=50")
      .then(response => {
        return {
          currencies: response.data
        };
      });
  },
  components: {
    Card
  }
};
</script>

<style scoped>
#cards {
  margin: auto;
  padding: 20px;
}
</style>
