<template>
  <div>
    <img :src="img" :width="size" alt="" />
    <p>
      Enter nickname :
      <input type="text" v-model="nickname" @keyup.enter="displayNickname" />
    </p>
    <h1>name : {{ getFullname }}</h1>
    <p>nickname : {{ nicknameDisplayed }}</p>
    <p>age : {{ age }}</p>
    <p>address : <span v-html="address"></span></p>
    <p>salary : {{ salary }} Bath</p>
    <button @click="addSalary(5000)">up salary</button>
    <button @click="dropSalary(5000)">drop salary</button>
    <p>profit/year : {{ getProfit }} Bath</p>
    <p>Job position : {{ getDepartment }}</p>
    <ul>
      <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
    </ul>
    <p>Information</p>
    <ul>
      <li v-for="(item, key) in general" :key="key">{{ key }}: {{ item }}</li>
    </ul>
    <button @click="showData">Click for details</button>
    <button @click="increment(10)">ADD AGE</button>
    <button @click="decrement(5)">DROP AGE</button>

    <button @click="toggleVisible()">
      {{ isVisible ? "hide" : "more" }} detail
    </button>
    <article v-show="isVisible">
      <form @submit.prevent="submitForm">
        <label>Enter your favorite</label>
        <input type="text" v-model="favorite" placeholder="Your favorite..." />
        <button type="submit">ENTER</button>
      </form>
      <p>favorite: {{ favorite }}</p>
      <div v-if="collection.length != 0">
        <p>my collection</p>
        <ul>
          <p>My collection</p>
          <li v-for="(item, index) in collection" :key="index">{{ item }}</li>
        </ul>
      </div>
      <p v-else>No collection</p>
    </article>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstname: "Bank",
      lastname: "Mergency",
      nickname: "",
      nicknameDisplayed: "",
      favorite: "",
      age: 30,
      address: "<strong>Donmuang</strong>",
      img: "https://science.nasa.gov/wp-content/uploads/2023/05/sun-cartoon-crop.png?w=4096&format=png&crop=1",
      size: 200,
      hobby: ["play a game", "travel", "sleep"],
      general: { gender: "male", weight: 75, height: 180 },
      collection: [],
      isVisible: false,
      salary: 50000,
    };
  },
  methods: {
    showData() {
      alert(this.getFullname);
    },
    increment(value) {
      this.age += value;
    },
    decrement(value) {
      this.age = Math.max(0, this.age - value);
    },
    submitForm() {
      console.log("Favorite saved:", this.favorite);
      alert("Save Complete");
    },
    displayNickname() {
      this.nicknameDisplayed = this.nickname;
      this.nickname = "";
    },
    toggleVisible() {
      this.isVisible = !this.isVisible;
    },
    addSalary(value) {
      this.salary += value;
    },
    dropSalary(value) {
      this.salary = Math.max(0, this.salary - value);
    },
  },
  computed: {
    getFullname() {
      return `${this.firstname} ${this.lastname}`;
    },
    getProfit() {
      return this.salary * 12;
    },
    getDepartment() {
      return this.salary >= 35000 ? "project manager" : "gege programmer";
    },
  },
  watch: {
    salary(value) {
      if (value > 70000) {
        alert("salary is not over 50,000");
        this.salary = 20000;
      }
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
