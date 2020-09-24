<template>
  <div class="details">
    <!-- <router-link :to="{ name: 'Home' }" class="Home">Home</router-link> -->
    <button class="Home" @click="goHome">Home</button>
    <h1>Country Name: {{ locations.name }}</h1>
    <h4>Capital: {{ locations.capital }}</h4>
    <p>{{ locations.description }}</p>
    <div class="image">
      <img :src="require(`@/assets/${locations.image}`)" alt="image" />
    </div>
  </div>
</template>

<script>
import store from "@/store.js";
export default {
  props: ["name"],
  data() {
    return {
      countryName: this.name
    };
  },
  computed: {
    locations() {
      return store.locations.find(
        location => location.name === this.countryName
      );
    }
  },
  methods: {
    goHome() {
      this.$router.push("/");
    }
  }
};
</script>

<style>
.details {
  width: 600px;
  margin: 30px 100px;
  color: #fff;
}
h1 {
  margin: 15px 0;
  color: orange;
}
h4 {
  margin-bottom: 12px;
}
p {
  margin-bottom: 12px;
}
.image {
  width: 100%;
}
.image img {
  width: 100%;
}
.Home {
  padding: 10px 15px;
  border: none;
  color: #fff;
  background: orangered;
  border-radius: 3px;
  outline: none;
  text-decoration: none;
  font-size: 14px;
}
</style>