<script setup lang="ts">
//import 
import { reactive } from "@vue/reactivity";
//import { onMounted } from "@vue/runtime-core";
import axios from "axios";


// user type 
interface User {
  name: string,
  surname: string,
  email: string,
  gender: string,
  picture: string
}
//state 
const state: User =  reactive({
  name: "John",
  surname: "Doe",
  email: "john@gmail.com",
  gender: "male",
  picture: "https://randomuser.me/api/portraits/men/11.jpg",
});
//

//get random user 
const getUser = () => {
  axios.get("https://randomuser.me/api").then((res) => {
    state.name = res.data.results[0].name.first;
    state.surname = res.data.results[0].name.last;
    state.email = res.data.results[0].email;
    state.gender = res.data.results[0].gender;
    state.picture = res.data.results[0].picture.large;
  });
};

//onMounted(getUser) windows loading api request 
</script>

<template>
  <div class="container">
    <img :class="state.gender" :src="state.picture" loading="lazy" :title="state.name" />
    <h1>{{ state.name }} {{ state.surname }}</h1>
    <h3>{{ state.email }}</h3>
    <button :class="state.gender" @click="getUser">Random User</button>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped >
.female {
  border: 5px solid #ffc0cb;
  background: #b46f7a;
}
h1,h3{
  font-size: 25px;
  font-weight: bold;
  color: white;
}

.male {
  border: 5px solid #87cefa;
  background: #2682bb;
}

img {
  border-radius: 50%;
}

img:active,
img:hover {
  opacity: 0.7;
}

button {
  padding: 1rem 2rem;
  border-radius: 0.5rem;
  color: #fff;
  cursor: pointer;
}

button:hover {
  transform: scale(1.1);
}

button:active {
  transform: translateY(2px);
}
</style>
