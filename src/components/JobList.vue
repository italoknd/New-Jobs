<template>
  <div class="job-list">
    <p>Ordered by: {{ props.order }}</p>
    <ul>
      <li v-for="{ title, location, salary, id } in jobs" :key="id">
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
    </ul>
  </div>
</template>

<script setup lang="ts">
import { PropType } from "vue";
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
</style>
