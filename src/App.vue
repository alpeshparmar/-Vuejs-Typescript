<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo">
        <h1>Jobs</h1>
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

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'
import JobList from './components/JobList.vue'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'Fullstack developer ', location: 'Surat', salary: 100000, id: '1' },
      { title: 'Frontend developer', location: 'Surat', salary: 22000, id: '2' },
      { title: 'Backend developer', location: 'Surat', salary: 30000, id: '3' },
      { title: 'HR manager', location: 'Delhi', salary: 20000, id: '4' },
      { title: 'prison guard', location: 'Ahemdabad', salary: 3000, id: '5' }
    ])
    const order = ref<OrderTerm>('title')
    console.log('order',order);
    

    const handleClick = (term: OrderTerm) => {
      order.value = term
      console.log("handleClick",term);
    }
    
    return { jobs, order, handleClick }
    
  }
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
    color: #2e2e2e;
    border: 3px solid #16ce93;
    background-color: #005aff2e;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
    margin-top: 6px;

  }
  @media (min-width: 320px) and (max-width: 481px) {
    .order {
   display: grid;
  }
}
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
