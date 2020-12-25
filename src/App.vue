<template>
  <div id="app" style="max-height:300px">
    <amplify-chatbot v-bind:chatbotConfig="chatbotConfig"></amplify-chatbot>
  </div>
</template>

<script>
import { Interactions } from "aws-amplify";
export default {
  name: "App",
  data: () => ({
    chatbotConfig: {
      bot: "OrderFlowers_dev",
      clearComplete: false,
    },
  }),
  mounted() {
    Interactions.onComplete("OrderFlowers_dev", this.handleComplete);
  },
  methods: {
    handleComplete(err) {
      if (err) {
        alert("bot conversation failed");
        return;
      }
      //alert("done: " + JSON.stringify(confirmation, null, 2));
      //return "Flower Order Complete. Thank you!";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>