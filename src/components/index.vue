<template>
  <div>
    <div class="columns">
      <div ref="main" class="main column is-three-quarter">
        <span class="pl-3 is-size-1 myTitle"
          ><span class="has-text-grey ">Watch</span>Weather</span
        >
        <p>{{ quote }}</p>
      </div>
      <div class="column is-one-quarter has-background-grey-dark"></div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      quote: null,
      image: null,
      forecast: null,
    };
  },
  beforeMount() {
    axios.get("https://api.quotable.io/random").then((response) => {
      this.quote = response.data.content;
    });
    axios
      .get(
        "https://api.unsplash.com/photos/random?client_id=4j3NCVWHWBF6uM9LlfrF_NQvO8J5AFOpvHd9lT6ZnzI&query=rain"
      )
      .then((response) => {
        this.image = response.data.urls.full;
        this.$refs["main"].style.background = `url(${this.image})`;
        console.log(response.data);
      });
    // axios.get('', {
    //   headers: {},
    //   params: {}
    // })
    axios
      .get(
        "https://api.openweathermap.org/data/2.5/onecall?lat={lat}&lon={lon}&exclude={part}&appid={API key}"
      )
      .then((response) => {
        // this.forecast = response.
      });
  },
  methods: {},
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap");

template {
  height: 100vh;
  padding: 0;
  margin: 0;
}
.main {
  /* background-image: url("../assets/iresh1.jpeg"); */
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: 100%;
  height: 100vh;
}
.myTitle {
  font-family: "Bebas Neue", cursive;
}
</style>
