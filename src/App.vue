<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>IT jobs - France</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>

    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";
import JobsList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobsList },

  setup() {
    // const state = reactive({
    //   name : 'Link',
    //   age: 25 as string | number

    // })

    // state.name = 'Shaun'
    // state.age = '26'

    // return { ...toRefs(state)}

    // const name = ref('Link')
    // const age = ref<number | string>(25)

    // return { name, age}

    const jobs = ref<Job[]>([
      {
        title: "Développeur Full Stack",
        location: "Paris",
        salary: 30000,
        id: "1",
      },
      {
        title: "Chef de Projet CRM",
        location: "Nantes",
        salary: 40000,
        id: "2",
      },
      {
        title: "Ingénieur systèmes et réseaux",
        location: "Lyon",
        salary: 35000,
        id: "3",
      },
      {
        title: "Technicien systèmes et réseau",
        location: "Marseille",
        salary: 21000,
        id: "4",
      },
      {
        title: "Data Scientist",
        location: "Toulouse",
        salary: 32000,
        id: "5",
      },
    ]);
    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header .title {
  display: flex;
  justify-content: center;
}
header h1 {
  font-size: 3em;
}
</style>
