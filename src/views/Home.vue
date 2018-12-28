<template>
  <div class="home">
    <Quote></Quote>
  </div>
</template>

<script>
var unirest = require("unirest");
import Quote from "@/components/Quote.vue";

export default {
  name: "home",
  components: {
    Quote
  },
  data() {
    return {};
  }
};
</script>
<style scoped lang='scss'>
@import "../../public/styles.scss";
</style>
