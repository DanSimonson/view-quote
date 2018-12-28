<template>
  <div class="quote">
    <div id="quote-box">
      <transition appear name="fade">
        <div class="wrap-one">
          <p id="text">{{quote}}</p>
          <p id="author">{{author}}</p>
        </div>
      </transition>
      <div class="wrap-two">
        <a id="new-quote" class="btn" @click="getQuote">New Quote</a>
        <a
          id="tweet-quote"
          class="btn"
          :href="'https://twitter.com/intent/tweet/?text=' + quote + ' '+author"
          target="_blank"
        >New Tweet</a>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
var unirest = require("unirest");

export default {
  name: "quote",
  components: {
    //HelloWorld
  },
  data() {
    return {
      quote: "",
      author: "",
      docState: "saved"
    };
  },
  methods: {
    getQuote() {
      let selfie = this;
      if (this.docState === "saved") {
        this.docState == "clicked";
      } else {
        this.docState == "saved";
      }

      unirest
        .get(
          "https://andruxnet-random-famous-quotes.p.rapidapi.com/?cat=famous&count=1"
        )
        .header(
          "X-RapidAPI-Key",
          "dbwwCjBPvPmshUBqeoOKBqHdFjw2p1h6XhFjsnyJvxW781cP5G"
        )
        .end(function(result) {
          //console.log(result.status, result.headers, result.body);
          if (result.status == 200) {
            //selfie.quotes.pop;
            selfie.quote = result.body[0].quote;
            selfie.author = result.body[0].author;
            //console.log(selfie.quote);
          } else {
            console.log("error: ", result.status);
          }
        });
    }
  },
  created() {
    this.getQuote();
  }
};
</script>
<style scoped lang='scss'>
@import "../../public/styles.scss";

#quote-box {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 4%;
}
.wrap-one {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  flex-direction: column;
  margin: 10px 5px 0 5px;
  font-size: 1.5rem;
  font-family: "Satisfy", cursive;
  letter-spacing: 0.05em;
  border-top: 1px solid rgba(0, 0, 0, 0.3);
  border-bottom: 1px solid rgba(0, 0, 0, 0.3);
}
.wrap-two {
  margin-top: 10px;
  display: flex;
  justify-content: space-around;
  margin-bottom: 10px;
}
.btn {
  background-color: blue;
  color: white;
  padding: 1em 1.5em;
  text-decoration: none;
  text-transform: uppercase;
  animation-fill-mode: backwards;
  border-radius: 3px;
  transition: background 0.3s linear 0s, color 0.3s;
}
.btn:hover {
  color: white;
  background-color: $Dark-green;
  cursor: pointer;
  box-shadow: 0 1rem 2rem rgba($Black, 0.15);
  transform: translateY(-2px);
}
.btn:active {
  button:active {
    box-shadow: 0 0.5rem 1rem rgba($Black, 0.15);
    transform: translateY(0);
  }
}
a#new-quote.btn {
  margin: 0 5px 0 5px;
  animation-name: moveInLeft;
  animation-duration: 3s;
  animation-delay: 1s;
  animation-timing-function: ease-out;
}
a#tweet-quote.btn {
  margin: 0 5px 0 5px;
  animation-name: moveInRight;
  animation-duration: 3s;
  animation-delay: 1s;

  animation-timing-function: ease-out;
}
@keyframes moveInLeft {
  0% {
    opacity: 0;
    transform: translateX(-100px);
  }
  100% {
    opacity: 1;
    transform: translate(0);
  }
}
@keyframes moveInRight {
  0% {
    opacity: 0;
    transform: translateX(100px);
  }
  100% {
    opacity: 1;
    transform: translate(0);
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8*/ {
  opacity: 0;
}
.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
</style>
