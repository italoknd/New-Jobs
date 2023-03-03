<template>
  <div class="job-list">
    <p>Ordered by: {{ props.order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="{ title, location, salary, id } in orderedJobs" :key="id">
        <h2>{{ title }} in {{ location }}</h2>
        <div class="salary">
          <p>{{ formatValue(salary) }}</p>
        </div>
        <div class="description">
          Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dolorem
          nobis sed quod minima necessitatibus unde, dignissimos corporis
          voluptatem repudiandae est aspernatur totam nulla dicta! Veritatis,
          iusto! Accusamus quia recusandae eius.
        </div>
      </li>
    </transition-group>
  </div>
</template>

<script setup lang="ts">
import { PropType, computed } from "vue";
import Job from "../types/Job";
import OrderTerm from "../types/OrderTerm";
import StrNum from "../types/StrNum";

//PROPS
const props = defineProps({
  jobs: {
    required: true,
    type: Array as PropType<Job[]>
  },
  order: {
    required: true,
    type: String as PropType<OrderTerm>
  }
});
const { jobs } = props;

//SPECIAL FUNCTIONS
const orderedJobs = computed(() => {
  return [...props.jobs].sort((a: Job, b: Job) => {
    return a[props.order] > b[props.order] ? 1 : -1;
  });
});
//FUNCTIONS
const formatValue = (val: StrNum): string => {
  return val.toLocaleString("pt-BR", {
    style: "currency",
    currency: "BRL"
  });
};
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}

.job-list > p{
  color: white;
  font-size: 20px;
}

.job-list ul {
  padding: 0;
}

.job-list li {
  list-style: none;
  background: white;
  padding: 1em;
  margin: 1em 0;
  border-radius: 4px;
}

.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}

.salary img {
  width: 30px;
}

.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}

ul > li {
  transition: .5s;
}

ul > li:hover{
  transform: scale(1.05);
  box-shadow: 9px 9px 7px rgba(0, 0, 0, 0.377);
  cursor: pointer;
}

.list{
  transition: all 1s;
}
</style>
