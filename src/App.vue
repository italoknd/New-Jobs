<script setup lang="ts">
import { reactive, ref } from "@vue/reactivity";
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
    salary: 7500,
    id: 1
  },
  {
    title: "Butler",
    location: "Michigan",
    salary: 4800,
    id: 1
  },
  {
    title: "farm-worker",
    location: "lon lon ranch",
    salary: 5800.0,
    id: 2
  },
  {
    title: "quarryman",
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
    <div>
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('salary')">Order by salary</button>
      <button @click="handleClick('location')">Order by location</button>
    </div>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<style scoped></style>
