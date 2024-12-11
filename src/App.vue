<template>
  <div>
    <img :src="img" :width="size" alt="">
    <h1>name : {{ getFullname() }}</h1>
    <p>age : {{ age }}</p>
    <p>address : <span v-html="address"></span></p>
    <ul>
      <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
    </ul>
    <p>infomation</p>
    <ul>
      <li v-for="([key, value], idx) in Object.entries(general)" :key="idx">
        {{ key }}: {{ value }}
      </li>
    </ul>
    <button @click="showData">Click</button>
    <button @click="increment">ADD</button>
    <button @click="decrement">DROP</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstname: "Bank",
      lastname: "Mergency",
      age: 30,
      address: "<strong>Donmuang</strong>",
      img: "https://science.nasa.gov/wp-content/uploads/2023/05/sun-cartoon-crop.png?w=4096&format=png&crop=1",
      size: 200,
      hobby: ["play a game", "travel", "sleep"],
      general: {gender : "male", weight: 75, height: 180},
    };
  },
  methods: {
    getFullname() {
      return `${this.firstname} ${this.lastname}`;
    },
    showData(){
      alert(this.getFullname())
    },
    increment(){
      this.age++
    },
    decrement(){
      this.age--
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
