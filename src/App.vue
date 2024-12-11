<template>
  <div>
    <img v-bind:src="img" :width="size" alt="">
    <h1>name : {{ getFullname() }}</h1>
    <p>address : <span v-html="address"></span></p>
    <ul>
      <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstname: "Bank",
      lastname: "Mergency",
      address: "<strong>Donmuang</strong>",
      img: "https://science.nasa.gov/wp-content/uploads/2023/05/sun-cartoon-crop.png?w=4096&format=png&crop=1",
      size: 200,
      hobby: ["play a game", "travel", "sleep"]
    };
  },
  methods: {
    getFullname() {
      return `${this.firstname} ${this.lastname}`;
    }
  }
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
