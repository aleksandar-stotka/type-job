<template>
  <div class="app">
    <button @click="handleClick('title')">order by title</button>
    <button @click="handleClick('location')">order by location</button>
    <button @click="handleClick('salary')">order by salary</button>
    
   <JobsList :jobs="jobs" :order="order"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref} from 'vue';
import job from "./types/job"
import JobsList from './components/JobsList.vue';
import orderTerm from '@/types/orderTerm'
export default defineComponent({
  name: 'App',
  components: {JobsList},
  setup() {
    
   const jobs = ref<job[]>([
    {title:'farm worker',location:'san francisko',salary:333,id:"1"},
    {title:'drumer',location:'d hisar',salary:223,id:"2"},
    {title:'pro bike',location:'Bitola',salary:1000,id:"3"},
    {title:'eri worker',location:'Struga',salary:500,id:"4"},
    {title:'guitarist',location:'Belgrad',salary:444,id:"5"}
   ])
  const order = ref<orderTerm>("title")
   const handleClick = (term:orderTerm) => {
    order.value = term
          
   }
     return {jobs,handleClick,order}
  },
 
 
});
</script>

<style scoped>
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

</style>
