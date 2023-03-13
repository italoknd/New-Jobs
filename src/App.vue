<script setup lang="ts">
import { ref } from "vue";
import IJob from "./types/Job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/JobList.vue";

// const state = reactive({
//   name: "Link" as string,
//   age: 25 as number | number
// });

// const end = ref<object>({
//   bairro: "Monte das Oliveiras" as string,
//   numero: 122 as number | string
// });

const jobs = ref<IJob[]>([
  {
    title: "Software Developer",
    location: "New York City",
    salary: 7500.0,
    id: 1
  },
  {
    title: "Butler",
    location: "Michigan",
    salary: 12500.0,
    id: 2
  },
  {
    title: "Farm-worker",
    location: "lon lon ranch",
    salary: 5800.0,
    id: 2
  },
  { 
    title: "Quarryman",
    location: "death mountain",
    salary: 7000.0,
    id: 3
  }
]);
let order = ref<OrderTerm>("title");

const handleClick = (term: OrderTerm) => {
  order.value = term;
};
</script>

<template>
  <div>
    <header>
      <div class="title">
        <h1>Newest Jobs!</h1>
        <p>Everyday a new job and a new opportunite for you!</p>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<style scoped>
.title{
  background: white;
  padding: 20px;
  border-radius: 4px;
  max-width: 960px;
  margin: 10px auto 0 auto;
}

header {
  text-align: center;
}

header .order {
  margin-top: 20px;
}

button {
  margin: 0 10px;
  color: #fff;
  border: 2px solid #17bf66;
  background: #17bf66;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  transition: 0.5s;
  box-shadow: 2.5px 2.5px 5px rgba(0, 0, 0, 0.329);
}

button:hover {
  transform: scale(1.1);
  box-shadow: 4.5px 4.5px 5px rgba(0, 0, 0, 0.329);
}
</style>
