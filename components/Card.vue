<template>
    <div>
        <md-card md-with-hover>
      <md-ripple>
        <md-card-header>
          <div class="md-title">{{name}}</div>
          <div class="md-subhead">{{price_usd}}</div>
        </md-card-header>

        <md-card-content :class="color">
          {{percent_change_1h}}
        </md-card-content>

       
      </md-ripple>
    </md-card>
    </div>
</template>

<script>
export default {
  props: ["name", "price_usd", "percent_change_1h"],

  computed: {
    color() {
      return this.percent_change_1h > 0 ? "inc" : "dec";
    }
  }
};
</script>

<style scoped>
.inc {
  color: green;
}
.dec {
  color: red;
}
</style>



