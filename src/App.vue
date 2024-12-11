<template>
  <div>
    <img :src="img" :width="size" alt="">
    <p>Enter nickname : <input type="text" v-model="nickname" @keyup.enter="displayNickname"></p>
    <h1>name : {{ getFullname() }}</h1>
    <p>nickname : {{ nicknameDisplayed }}</p>
    <p>age : {{ age }}</p>
    <p>address : <span v-html="address"></span></p>
    <ul>
      <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
    </ul>
    <p>Information</p>
    <ul>
      <li v-for="([key, value], idx) in Object.entries(general)" :key="idx">
        {{ key }}: {{ value }}
      </li>
    </ul>
    <button @click="showData">Click for details</button>
    <button @click="increment(10)">ADD</button>
    <button @click="decrement(5)">DROP</button>
    <form @submit.prevent="submitForm">
      <label>Enter your favorite</label>
      <input type="text" v-model="favorite" placeholder="Your favorite...">
      <button type="submit">ENTER</button>
    </form>
    <p>favorite: {{ favorite }}</p>
    <div v-if="collection.length != 0">
      <p> my collection</p>
      <ul>
        <p>My collection</p>
        <li v-for="(item, index) in collection" :key="index">{{ item }}</li>
      </ul>
    </div>
    <p v-else>No collection</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      firstname: "Bank",
      lastname: "Mergency",
      nickname: "",
      nicknameDisplayed: "",  // จะใช้แสดงชื่อเล่นที่กด Enter
      favorite: "",
      age: 30,
      address: "<strong>Donmuang</strong>",
      img: "https://science.nasa.gov/wp-content/uploads/2023/05/sun-cartoon-crop.png?w=4096&format=png&crop=1",
      size: 200,
      hobby: ["play a game", "travel", "sleep"],
      general: { gender: "male", weight: 75, height: 180 },
      collection:[],
    };
  },
  methods: {
    getFullname() {
      return `${this.firstname} ${this.lastname}`;
    },
    showData() {
      alert(this.getFullname());
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
      this.nicknameDisplayed = this.nickname;  // ตั้งค่าชื่อเล่นให้แสดงหลังจากกด Enter
      this.nickname = "";  // ลบข้อความใน input หลังจากกด Enter
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
