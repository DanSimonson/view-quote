<template>
  <div class="home">
    <Quote></Quote>
    <Footer></Footer>
  </div>
</template>

<script>
var unirest = require("unirest");
import Quote from "@/components/Quote.vue";
import Footer from "@/components/Footer.vue";

export default {
  name: "home",
  components: {
    Quote,
    Footer
  },
  data() {
    return {};
  }
};
</script>
<style scoped lang='scss'>
@import "../../public/styles.scss";
</style>
